
# StarkNet Development Environment Setup

This README provides instructions for setting up a local development environment for StarkNet using the StarkNet Devnet and Protostar tools.

## Prerequisites

Before proceeding, ensure you have Docker installed on your system.

## Running StarkNet Devnet

Start the StarkNet Devnet using Docker with the following command:

```bash
docker run -p 5050:5050 shardlabs/starknet-devnet-rs --seed 0
```

This command runs the StarkNet Devnet on port 5050 and initializes it with a seed value of `0`.

## Deploying Contracts with Protostar

To deploy contracts using Protostar, follow these steps:

1. **Build the Contract:**

   Build your contract using the `protostar build-cairo0` command:

   ```bash
   protostar build-cairo0
   ```

   This command compiles your Cairo contracts and prepares them for deployment.

2. **Set Environment Variable:**

   Set the `PROTOSTAR_ACCOUNT_PRIVATE_KEY` environment variable to your private key:

   ```bash
   export PROTOSTAR_ACCOUNT_PRIVATE_KEY=0x71d7bb07b9a64f6f78ac4c816aff4da9
   ```

3. **Deploy the Contract:**

   Use the `protostar declare-cairo0` command to deploy your contract:

   ```bash
   protostar declare-cairo0 --account-address 0x64b48806902a367c8598f4f95c305e8c1a1acba5f082d294a43793113115691 --max-fee auto --gateway-url http://localhost:5050/ --chain-id 1536727068981429685321 build/main.json
   ```

   This command deploys your contract (specified in `build/main.json`) to the local StarkNet chain.

## Notes

- The `--seed` parameter in the `docker run` command is used to initialize the blockchain with a deterministic state.
- The `PROTOSTAR_ACCOUNT_PRIVATE_KEY` should be kept secure and not shared.
- The `--account-address` in the `protostar` command should be replaced with your account address.
- The `--chain-id` specifies the chain ID for the StarkNet network.

## Conclusion

These instructions set up a local development environment for StarkNet, allowing you to deploy and test smart contracts locally.
