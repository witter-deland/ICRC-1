# ICRC-1 Token Standard

The ICRC-1 is a standard for Fungible Tokens on the [Internet Computer](internetcomputer.org).

## Methods

### name

Returns the name of the token, e.g. `MyToken`.

```
name: () -> (text) query;
```

### symbol

Returns the symbol of the token, e.g. `ICP`.

```
symbol: () -> (text) query;
```

### decimals

Returns the number of decimals the token uses, e.g. `8`, means to divide the token amount by `100000000` to get its user representation.

```
decimals: () -> (nat32) query;
```

### totalSupply

Returns the total token supply.

```
totalSupply: () -> (nat32) query;
```

### balanceOf

Returns the balance of the account given as argument.

```
balanceOf: (record { Principal; SubAccount; }) -> (nat64) query;
```

### transfer

Transfers `amount` of tokens from the account `(caller, from_subaccount)` to the account `(to_principal, to_subaccount)`.

```
type TransferArgs = record {
    from_subaccount: opt SubAccount;
    to_principal: Principal;
    to_subaccount: opt SubAccount;
    amount: nat64;
};

transfer: (TransferArgs) -> (variant { Ok: nat64; Err: TransferError; });
```

The result is either the block index of the transfer or an error. The list of errors is:

```
type TransferError = variant {
    // TODO
    GenericError: text,
};
```