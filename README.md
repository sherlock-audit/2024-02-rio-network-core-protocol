
# Rio Vesting Core Protocol contest details

- Join [Sherlock Discord](https://discord.gg/MABEWyASkp)
- Submit findings using the issue page in your private contest repo (label issues as med or high)
- [Read for more details](https://docs.sherlock.xyz/audits/watsons)

# Q&A

### Q: On what chains are the smart contracts going to be deployed?
Ethereum Mainnet
___

### Q: Which ERC20 tokens do you expect will interact with the smart contracts? 
Standard ERC20 tokens with no less than 6 decimals and no more than 18 decimals. Rebasing tokens, fee-on-transfer tokens, and tokens with multiple entry points are NOT supported.
___

### Q: Which ERC721 tokens do you expect will interact with the smart contracts? 
None
___

### Q: Do you plan to support ERC1155?
No
___

### Q: Which ERC777 tokens do you expect will interact with the smart contracts? 
None
___

### Q: Are there any FEE-ON-TRANSFER tokens interacting with the smart contracts?

No
___

### Q: Are there any REBASING tokens interacting with the smart contracts?

No
___

### Q: Are the admins of the protocols your contracts integrate with (if any) TRUSTED or RESTRICTED?
TRUSTED
___

### Q: Is the admin/owner of the protocol/contracts TRUSTED or RESTRICTED?
TRUSTED
___

### Q: Are there any additional protocol roles? If yes, please explain in detail:
1. Contract Owner: All protocol contracts are owned by the RioDAO, which uses the Llama governance framework.
2. Operator Manager: Within the Operator Registry, operators are managed by "operator managers". These entities engage with the registry to manage configurations specific to their operations. They are authorized to designate an earnings receiver, appoint a new manager through a two-step process, verify validator withdrawal credentials, add validator details (keys/signatures), and remove pending validator details.
3. Security Daemon: The security daemon has permission to remove duplicate or invalid validator keys during the validator key review period.
4. Proof Uploader: The proof uploader has permission to verify validator withdrawal credentials within the Operator Registry.
___

### Q: Is the code/contract expected to comply with any EIPs? Are there specific assumptions around adhering to those EIPs that Watsons should be aware of?
No
___

### Q: Please list any known issues/acceptable risks that should not result in a valid finding.
Issues related to the RioDAO's ability to upgrade contracts should not be considered valid. All calls that have the ability to rug users will be behind a sufficient timelock.
___

### Q: Are there any off-chain mechanisms or off-chain procedures for the protocol (keeper bots, input validation expectations, etc)?
Yes, there are several:

1. A rebalance bot that calls `rebalance` on the Coordinator contract once the rebalance delay has elapsed (roughly once every 24 hours).
2. A security daemon bot that monitors validator key uploads and has permission to remove invalid, pending keys.
3. A proof uploader bot, which verifies validator credentials as they are funded, and verifies and processes full and partial validator withdrawals within EigenPods.
___

### Q: In case of external protocol integrations, are the risks of external contracts pausing or executing an emergency withdrawal acceptable? If not, Watsons will submit issues related to these situations that can harm your protocol's functionality.
Yes, the risks associated with EigenLayer and EigenLayer's governance are considered acceptable.
___

### Q: Do you expect to use any of the following tokens with non-standard behaviour with the smart contracts?
- We plan to support tokens with no less than 6 decimals and no more than 18 decimals.
- Tokens may not return a bool on ERC20 methods (e.g. USDT)
- Tokens may have approval race protections (e.g. USDT)
___

### Q: Add links to relevant protocol resources
Rio Network Documentation: https://docs.rio.network/
EigenLayer Documentation: https://docs.eigenlayer.xyz/
Llama Documentation: https://docs.llama.xyz/
___



# Audit scope


[rio-sherlock-audit @ 02b9be62a676b2383070fa956a70e459eb2f5c5a](https://github.com/rio-org/rio-sherlock-audit/tree/02b9be62a676b2383070fa956a70e459eb2f5c5a)
- [rio-sherlock-audit/contracts/oracle/ChainlinkPriceFeed.sol](rio-sherlock-audit/contracts/oracle/ChainlinkPriceFeed.sol)
- [rio-sherlock-audit/contracts/restaking/RioLRT.sol](rio-sherlock-audit/contracts/restaking/RioLRT.sol)
- [rio-sherlock-audit/contracts/restaking/RioLRTAVSRegistry.sol](rio-sherlock-audit/contracts/restaking/RioLRTAVSRegistry.sol)
- [rio-sherlock-audit/contracts/restaking/RioLRTAssetRegistry.sol](rio-sherlock-audit/contracts/restaking/RioLRTAssetRegistry.sol)
- [rio-sherlock-audit/contracts/restaking/RioLRTCoordinator.sol](rio-sherlock-audit/contracts/restaking/RioLRTCoordinator.sol)
- [rio-sherlock-audit/contracts/restaking/RioLRTDepositPool.sol](rio-sherlock-audit/contracts/restaking/RioLRTDepositPool.sol)
- [rio-sherlock-audit/contracts/restaking/RioLRTIssuer.sol](rio-sherlock-audit/contracts/restaking/RioLRTIssuer.sol)
- [rio-sherlock-audit/contracts/restaking/RioLRTOperatorDelegator.sol](rio-sherlock-audit/contracts/restaking/RioLRTOperatorDelegator.sol)
- [rio-sherlock-audit/contracts/restaking/RioLRTOperatorRegistry.sol](rio-sherlock-audit/contracts/restaking/RioLRTOperatorRegistry.sol)
- [rio-sherlock-audit/contracts/restaking/RioLRTRewardDistributor.sol](rio-sherlock-audit/contracts/restaking/RioLRTRewardDistributor.sol)
- [rio-sherlock-audit/contracts/restaking/RioLRTWithdrawalQueue.sol](rio-sherlock-audit/contracts/restaking/RioLRTWithdrawalQueue.sol)
- [rio-sherlock-audit/contracts/restaking/base/RioLRTCore.sol](rio-sherlock-audit/contracts/restaking/base/RioLRTCore.sol)
- [rio-sherlock-audit/contracts/restaking/storage/RioLRTOperatorRegistryStorageV1.sol](rio-sherlock-audit/contracts/restaking/storage/RioLRTOperatorRegistryStorageV1.sol)
- [rio-sherlock-audit/contracts/utils/Array.sol](rio-sherlock-audit/contracts/utils/Array.sol)
- [rio-sherlock-audit/contracts/utils/Asset.sol](rio-sherlock-audit/contracts/utils/Asset.sol)
- [rio-sherlock-audit/contracts/utils/Constants.sol](rio-sherlock-audit/contracts/utils/Constants.sol)
- [rio-sherlock-audit/contracts/utils/LRTAddressCalculator.sol](rio-sherlock-audit/contracts/utils/LRTAddressCalculator.sol)
- [rio-sherlock-audit/contracts/utils/Memory.sol](rio-sherlock-audit/contracts/utils/Memory.sol)
- [rio-sherlock-audit/contracts/utils/OperatorOperations.sol](rio-sherlock-audit/contracts/utils/OperatorOperations.sol)
- [rio-sherlock-audit/contracts/utils/OperatorRegistryV1Admin.sol](rio-sherlock-audit/contracts/utils/OperatorRegistryV1Admin.sol)
- [rio-sherlock-audit/contracts/utils/OperatorUtilizationHeap.sol](rio-sherlock-audit/contracts/utils/OperatorUtilizationHeap.sol)
- [rio-sherlock-audit/contracts/utils/ValidatorDetails.sol](rio-sherlock-audit/contracts/utils/ValidatorDetails.sol)


