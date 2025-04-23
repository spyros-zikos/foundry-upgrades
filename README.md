# Getting Started

## Requirements

- git
- foundry

## Quickstart

```
git clone https://github.com/spyros-zikos/foundry-upgrades
cd foundry-upgrades
forge build
```
Set up .env (see below)
(To deploy:
  make deploy ARGS="--network sepolia"
  make upgrade ARGS="--network sepolia")
```
cast call 0xE49FFDC9815bc85D81E3f5d7fCa8ccBe8b61cB1b "getNumber()" --rpc-url $SEPOLIA_RPC_URL
cast send 0xE49FFDC9815bc85D81E3f5d7fCa8ccBe8b61cB1b "setNumber(uint256)" 88 --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY
cast call 0xE49FFDC9815bc85D81E3f5d7fCa8ccBe8b61cB1b "getNumber()" --rpc-url $SEPOLIA_RPC_URL
```

# Usage

## Start a local node

```
make anvil
```

## Library

If you're having a hard time installing the chainlink library, you can optionally run this command. 

```
forge install smartcontractkit/chainlink-brownie-contracts@0.6.1 --no-commit
forge install openzeppelin/openzeppelin-contracts-upgradable --no-commit
```

## Deploy

This will default to your local node. You need to have it running in another terminal (by executing the command 'anvil') in order for it to deploy.

```
make deploy
```

## Deploy - Other Network

[See below](#deployment-to-a-testnet-or-mainnet)

## Testing

```
forge test
```

or

```
forge test --fork-url $SEPOLIA_RPC_URL
```

### Test Coverage

```
forge coverage
```

# Deployment to a testnet or mainnet

Deployed BoxV1 contract address on sepolia: 0xc05D839Fcc9aa7cB51445655809164A44e6C35fb
Deployed Proxy contract address on sepolia: 0xE49FFDC9815bc85D81E3f5d7fCa8ccBe8b61cB1b
Deployed BoxV2 contract address on sepolia: 0x8708D4De8335A8Fe652199Cd8473a1e14c88E0f8


1. Setup environment variables

You'll want to set your `SEPOLIA_RPC_URL` and `PRIVATE_KEY` as environment variables. You can add them to a `.env` file.

- `PRIVATE_KEY`: The private key of your account.
  **NOTE:** FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
- `SEPOLIA_RPC_URL`: This is url of the sepolia testnet node you're working with. You can get setup with one for free from [Alchemy](https://alchemy.com)

Optionally, add your `ETHERSCAN_API_KEY` if you want to verify your contract on [Etherscan](https://etherscan.io/).

2. Get testnet ETH

Head over to [faucets.chain.link](https://faucets.chain.link/) and get some testnet ETH. You should see the ETH show up in your metamask.

3. Deploy

```
make deploy ARGS="--network sepolia"
```

4. Upgrade

```
make upgrade ARGS="--network sepolia"
```

## Scripts

We can directly use the `cast` command to interact with the contract.

For example, on Sepolia:

1. Get the value of variable 'number'
```
cast call 0xE49FFDC9815bc85D81E3f5d7fCa8ccBe8b61cB1b "getNumber()" --rpc-url $SEPOLIA_RPC_URL

```
2. Set the value of variable 'number'
```
cast send 0xE49FFDC9815bc85D81E3f5d7fCa8ccBe8b61cB1b "setNumber(uint256)" 88 --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY
```
