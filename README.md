## Router Protocol

<!-- <p align="center" >

<img src="https://user-images.githubusercontent.com/124175970/224509096-12e4864a-6819-4c8c-8998-41c7a96ba026.jpg" />
  </p> -->

<!-- ![router-protocol-crypto-ninjas](https://user-images.githubusercontent.com/124175970/224509096-12e4864a-6819-4c8c-8998-41c7a96ba026.jpg) -->

<img src="https://user-images.githubusercontent.com/124175970/224509096-12e4864a-6819-4c8c-8998-41c7a96ba026.jpg" width="8000000em" height="400em" />


# `Company Information`

Router Protocol is a solution introduced to address the issues hindering the usability of cross-chain liquidity migration in the DeFi ecosystem. It acts as a bridge connecting various layer 1 and layer 2 blockchains, allowing for the flow of contract-level data across them. The Router Protocol can either transfer tokens between chains or initiate operations on one chain and execute them on another.

# ⭐️ `Star us`

If this repository helps you build cross-chain dapps faster and easier - please star this project, every star makes us very happy!

# 🤝 `Need help?`

If you need help or have other some questions - don't hesitate to write in our discord channel and we will check asap. [Discord link](https://discord.gg/z7v3mrUE). The best thing about this is the super active community ready to help at any time! We help each other.

# 🤝 `Clone or fork this repository`

```sh
https://github.com/router-resources/CrossChain-NFT-Cookbook
```
# `CrossChain ERC-721`

## `What is an ERC721 Token ?`

![_117548721_nfts2](https://user-images.githubusercontent.com/124175970/224860849-f037eb49-0288-49b8-a922-e08015b5280a.jpg)

ERC721 Tokens are digital assets that are created using the Ethereum blockchain technology. They are programmable tokens that can be used to represent various types of assets, such as loyalty points, shares of stock, or even cryptocurrencies. ERC20 Tokens are fungible, which means that each token has the same value and can be exchanged for another token of the same value.

The "ERC721" part of the name refers to the technical standard that is used to create and manage these tokens. This standard defines the rules for creating new tokens and the functions that can be used to transfer and manage them.

Here's an example of **Bored Ape** NFT series :-

![bored-ape-yacht-club-nft (1)](https://user-images.githubusercontent.com/124175970/224862305-ca762b98-a29c-4d6f-9693-9642f7c63ae1.gif)


## `How to make a simple NFT ?`

**ERC721 Standard**

![1_-Aq82tW0D4c9Xn8zHRYecw](https://user-images.githubusercontent.com/124175970/224863210-5b6262b9-e793-49ee-b1f0-1158eda92cf0.png)

ERC721 is a standard for creating non-fungible tokens on the Ethereum blockchain. The ERC721 standard is like a set of rules that all NFTs on the Ethereum blockchain must follow. Think of it like a recipe for making a cake - you need certain ingredients and instructions to make sure it turns out right.

ERC721 defines a specific set of functions that NFTs must have, like the ability to be transferred from one owner to another, the ability to check who owns a particular NFT, and the ability to create new NFTs. These functions are like different steps in the recipe.

**ERC721 Functions**

Some of the functions included in the ERC721 standard are:

**mint**: This function creates a new token and assigns it to an owner.

**transfer**: This function allows the owner of a token to transfer ownership to another address.

**balanceOf**: This function returns the number of tokens owned by a specific address.

**ownerOf**: This function returns the address of the current owner of a specific token.

**approve**: This function allows an address to approve another address to transfer ownership of a specific token.

**safeTransferFrom**: This function transfers ownership of a token from one address to another, but also includes additional safety checks to ensure the transfer is successful.

**What is OpenZeppelin ?**

Instead of writing all the code for creating an NFT from scratch, developers can use OpenZeppelin's pre-written code to make their own NFTs. This can save a lot of time and effort, and can also help ensure that the code works correctly and is secure.

It's kind of like using Lego blocks to build something - instead of making each block from scratch, you can just use pre-made blocks to build something faster and easier.

With OpenZeppelin, developers can just follow the pre-written code to create their own NFTs without having to start from scratch.

**Simple ERC721 contract using Openzeppelin**

```sh
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.9;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/token/ERC721/extensions/ERC721Burnable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/Counters.sol";

contract MyToken is ERC721, ERC721Burnable, Ownable {
    using Counters for Counters.Counter;

    Counters.Counter private _tokenIdCounter;

    constructor() ERC721("MyToken", "MTK") {}

    function _baseURI() internal pure override returns (string memory) {
        return "<paste the url here>";
    }

    function safeMint(address to) public onlyOwner {
        uint256 tokenId = _tokenIdCounter.current();
        _tokenIdCounter.increment();
        _safeMint(to, tokenId);
    }
}
```

The contract is making use of the OpenZeppelin library which includes pre-written functions that make it easier to create NFTs.

Then the name and symbol of the NFT is given as parameters to the constructor.It's using three different pre-written contracts from OpenZeppelin:

**ERC721**: This is the main contract for creating NFTs. It defines the basic functions that NFTs should have, like the ability to be owned and transferred.

**ERC721Burnable** : This is an extension of ERC721 that allows the owner of an NFT to "burn" it, or destroy it completely. This can be useful for controlling the supply of an NFT.

**Ownable** : This is another extension of ERC721 that defines an "owner" for the NFT contract. Only the owner can perform certain functions, like creating new tokens.

The code also includes a "using" statement, which tells the contract to use a library called "Counters". This library includes a function called "Counter" that's used to keep track of the number of tokens that have been created.

The constructor function is defining the name and abbreviation of the NFT. The name is "MyToken" and the abbreviation is "MTK".

The "_baseURI" function is defining the URL where people can go to find more information about the NFT (metadata). This could be either IPFS or other decentralised storage networks. For this, you can make use of tools like [NFTUP](https://nft.storage/docs/how-to/nftup/)

The "safeMint" function is used to create new tokens and assign them to a specific owner. The owner of the NFT contract is the only one who can use this function. It uses the "Counter" function from the Counters library to keep track of the number of tokens that have been created. When a new token is created, the owner can assign it to a specific address.

You can use the above code and deploy using [Remix IDE](https://www.remix.ethereum.org) and Hurray !, you've made your own NFT .



## `What is a CrossChain NFT ?`

CrossChain NFTs are non-fungible tokens that can exist and be traded on multiple different blockchain networks. This means that an NFT created on one blockchain network, such as Ethereum, can be moved to and traded on another blockchain network, such as Binance Smart Chain or Polygon.

Imagine you have an NFT on the Ethereum blockchain that represents a piece of artwork. If you want to sell or trade that NFT on another blockchain network, you would need to create a new NFT on that network, which can be time-consuming and costly. However, with CrossChain NFTs, you can simply transfer the original NFT to the new blockchain network, enabling you to sell or trade it without having to go through the process of creating a new one.

<img width="461" alt="image" src="https://user-images.githubusercontent.com/124175970/224872315-6b455b3f-e822-400d-ab2d-cb81ad135f5d.png">


Router's crosstalk library: Provides functions that help to create cross-chain communication between different blockchain networks.



// SPDX-License-Identifier: UNLICENSED

From Solidity version ^0.6.8 SPDX license is introduced. You need to use SPDX-License-Identifier: <SPDX-License> in the first line of your contract with comments like shown above. Trust in smart contracts can be better established if their source code is available. Since making source code available always touches on legal problems with regards to copyright, the Solidity compiler encourages the use of machine-readable SPDX license identifiers. You can find all SPDX license lists here.

```sh 
pragma solidity >=0.8.0 <0.9.0;
```
Pragma is generally the first line of code within any Solidity file. pragma is a directive that specifies the compiler version to be used for current Solidity file. With the help of the pragma directive, you can choose the compiler version and target your code accordingly, as shown in the snippet above


```sh
import "@routerprotocol/evm-gateway-contracts/contracts/IDapp.sol";
import "@routerprotocol/evm-gateway-contracts/contracts/IGateway.sol";
import "@routerprotocol/evm-gateway-contracts/contracts/Utils.sol";
import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
```

By importing, we mean combining two solidity files which means that the two files just share their interface. You can call external and public functions of the imported contract but not the internal traits which is the case with inheritance.

```
import the ERC721.sol, ERC721URIStorage.sol and Ownable.sol contracts from openzeppelin/contracts

Import the IDapp.sol,Utils.sol and  IGateway.sol from evm-gateway-contract/contracts. 

// This is how we inherit any contract into our contract using `is` identifier.
contract XERC721 is ERC721, IDapp{
```

By Inheriting, we can access all the non-private members including state variables and internal methods of inherited contract. 

Inherit the ERC721.sol contract into your main contract (XERC721). 

Inherit the IDapp contract into your main contract (XERC721).


```sh
constructor(
    address payable gatewayAddress,
    string memory feePayerAddress
  ) ERC721("My Token", "MTK") {
    gatewayContract = IGateway(gatewayAddress)
    gatewayContract.setDappMetadata(feePayerAddress);
    owner = msg.sender;

  }
```


When we inherit a contract (which has a constructor) into our contract, we have to initiate its constructor like I have shown above. For instance, we had to inherit ERC721.sol. This file has its constructor that needs the name and symbol of the NFT. So we now need to provide that name and symbol through the constructor that we define in our contract because our contract is nothing but a logic written on the top of ERC721.sol code.

The constructor of the smart contract takes 2 parameters:
gatewayAddress - an address variable which holds the address of the gateway contract.
feePayerAddress - a string variable which holds the address on the Router Chain from which the fees is deducted.
Further, we pass gatewayAddress to IGateway function which sets the gateway address and call setDappMetadata function of gatewayContract which sets the feePayerAddress.
Finally, we set the owner to be the person who deployed the contract by the following command:-
owner = msg.sender;

```sh

function iReceive(
    string memory requestSender,
    bytes memory packet,
    string memory srcChainId
  ) external override returns (bytes memory) {}

function iAck(
    uint256 requestIdentifier,
    bool execFlag,
    bytes memory execData
  ) external override {}
				
				```

So, when we use the interface contracts into our contract, we are also liable to implement the above two functions mandatorily, otherwise our contract would not compile successfully. For now, I have kept the function implementations empty {}. We will add the logic into them according to our requirements as we move ahead with the project.


It is important to ensure that any code snippets for state variables are placed within the same smart contract that was imported and inherited in the previous step. This is because state variables need to be defined within a contract, and the inherited contracts and imported files define the structure of the contract that is being created.

State variables are variables that hold values that define the current state of the contract. They are declared at the contract level, outside any function, and are used to store data that can be accessed by multiple functions within the contract. Examples of state variables in an NFT contract may include the name of the NFT, the owner of the NFT, and the current supply of the NFT.

A constructor, on the other hand, is a special function that is called when the contract is deployed. It is used to initialize the state variables of the contract and set their initial values. The constructor function is defined with the same name as the contract, and it can take arguments that set the initial values of the state variables

Make sure that you continue putting the code snippets into the same smart contract that we started in the Import&Inherit step.



These are the different state variables that we have used in our contract. Each line has been explained, what it actually does.
address public admin;
Admin is the address that is to be used for access control purposes.




IGateway public gatewayContract;
gatewayContract is the address of the contract which will be used to interact with the Router Chain.




mapping(string => string) public ourContractOnChains;   
ourContractOnChains is a mapping that stores the addresses of the counterparts of our NFT contract on different chains. The chain Id is mapped to the contract address on that chain. Chain Id is the ID of the chain in string format.You can find them here https://lcd.testnet.routerchain.dev//router-protocol/router-chain/multichain/chain_config




```sh
	struct TransferParams {
   	 uint256 nftId;
   	 bytes recipient;
    	string uri;
  	}
```

TransferParams is a struct that holds the Id of the NFT, wallet address that will hold the NFT and the URI for the NFT.




Some static information is required for the request so that dapps don’t have to encode it on-chain, they can just send it as a parameter to their dapp depending on the destination chain Id passed by the user. The request metadata is a bytes encoded string consisting of the following parameters:
destGasLimit: Gas limit required for execution of the request on the destination chain. This can be calculated using tools like hardhat-gas-reporter. Here, in this case will are passing 500000 as the destGasLimit
destGasPrice: Gas price of the destination chain. This can be calculated using the RPC of destination chain. If you don’t want to calculate it, just send 0 in its place and Router Chain will handle the real time gas price for you. In this case, we will be passing 30000000000 as destGasPrice.
ackGasLimit: Gas limit required for execution of the acknowledgement coming from the destination chain back on the source chain. This can be calculated using tools like hardhat-gas-reporter. In this case, we will be passing 0 as ackGasLimit because we don’t want any acknowledgement to be sent back to the source chain.
ackGasPrice: Gas price of the destination chain. This can be calculated using the RPC of source chain.In this case, we will be passing 0 as ackGasPrice because we don’t want any acknowledgement to be sent back to the source chain.
relayerFees: This is similar to priority fees that one pays on other chains. Router chain relayers execute your requests on the destination chain. So if you want your request to be picked up by relayer faster, this should be set to a higher number. If you pass really low amount, the Router chain will adjust it to some minimum amount. In this case, we will be passing 0 as relayerFees
ackType: When the contract calls have been executed on the destination chain, the iDapp has the option to get an acknowledgement back to the source chain.In this case, we will be passing 0 as ackGasPrice because we don’t want any acknowledgement to be sent back to the source chain.


Actually,we provide the option to the user to be able to get this acknowledgement from the router chain to the source chain and perform some operation based on it.
ackType = 0: You don’t want the acknowledgement to be forwarded back to the source chain.
ackType = 1: You only want to receive the acknowledgement back to the source chain in case the calls executed successfully on the destination chain and perform some operation after that.
ackType = 2: You only want to receive the acknowledgement back to the source chain in case the calls errored on the destination chain and perform some operation after that.
ackType = 3: You only want to receive the acknowledgement back to the source chain in both the cases (success and error) and perform some operation after that.
isReadCall: We provide you the option to query a contract from another chain and get the data back on the source chain through acknowledgement. If you just want to query a contract on destination chain, set this to true. In this case, we will be setting this to false because we don’t want to query the contract from another chain and get the data back on the source chain through acknowledgement.
asmAddress: We also provide modular security framework for creating an additional layer of security on top of the security provided by Router Chain. These will be in the form of smart contracts on destination chain. The address of this contract needs to be passed in the form of string in this variable.In this case, we will be passing an empty string “” in asmAddress because we don’t want any additional security.

The request metadata can be constructed using the following code:
	
```sh
function getRequestMetadata(
    uint64 destGasLimit,
    uint64 destGasPrice,
    uint64 ackGasLimit,
    uint64 ackGasPrice,
    uint128 relayerFees,
    uint8 ackType,
    bool isReadCall,
    string calldata asmAddress
  ) public pure returns (bytes memory) {
    bytes memory requestMetadata = abi.encodePacked(
      destGasLimit,
      destGasPrice,
      ackGasLimit,
      ackGasPrice,
      relayerFees,
      ackType,
      isReadCall,
      asmAddress
    );
    return requestMetadata;
  }
```




The NFTs will be transferred across chains via the burn-mint technique, in which we mint NFTs for the receiver on the destination chain after burning NFTs from the source chain's user account.

Burning is the act of sending an NFT to a null address, and minting is the act of moving a null address NFT to the address of the recipient to create a brand-new NFT.

To achieve this, we shall create a public & payable function transferCrossChain that takes three parameters. But before that lets know more about various types(public, private, external, internal, pure, view) of solidity functions from here. 


Code
	
```sh

function transferCrossChain(
    string calldata destChainId,
    TransferParams calldata transferParams,
    bytes calldata requestMetadata
  ) public payable {
    require(
      keccak256(bytes(ourContractOnChains[destChainId])) !=
        keccak256(bytes("")),
      "contract on dest not set"
    );

    require(
      _ownerOf(transferParams.nftId) == msg.sender,
      "caller is not the owner"
    );

    // burning the NFT from the address of the user calling _burn function
    _burn(transferParams.nftId);

    // sending the transfer params struct to the destination chain as payload.
    bytes memory packet = abi.encode(transferParams);
    bytes memory requestPacket = abi.encode(
      ourContractOnChains[destChainId],
      packet
    );

    gatewayContract.iSend{ value: msg.value }(
      1,
      0,
      string(""),
      destChainId,
      requestMetadata,
      requestPacket
    );
  }
```

Let us know about the stuff that's going on here step by step;

```ssh
require(
      keccak256(bytes(ourContractOnChains[destChainId])) !=
        keccak256(bytes("")),
      "contract on dest not set"
    );
	
```
Making sure the counter contract set is not empty.
	
```sh
require(
      _ownerOf(transferParams.nftId) == msg.sender,
      "caller is not the owner"
    );
```


Making sure the person calling the function is the owner of the NFT that he wants to transfer: 


// burning the NFT from the address of the user calling this function
  _burn(id);
Burning the NFTs from the user's account: Using the _burn method specified in the Openzeppelin library's ERC-721 contract, we will burn the NFTs from the user's account before generating a cross-chain communication request to the destination chain.


```sh
  bytes memory packet = abi.encode(transferParams);
    bytes memory requestPacket = abi.encode(
      ourContractOnChains[destChainId],
      packet
    );
```


We encode transferParams in a variable called packet and further encode the packet  along with the destination contract address in a variable called requestPacket.This is the data we require to execute out our function or logic at the destination chain. 
We then call the iSend function of Router’s Gateway Contract that facilitates the transmission of a cross-chain message. Whenever users want to execute a cross-chain request, they can call this function by passing the required parameters.
version: Current version of Gateway contract which can be queried from the Gateway contract using the following function.
routeAmount: If one wants to transfer Route tokens along with the call, they will have to pass the amount of tokens to be transferred here.
routeRecipient: If one wants to transfer Route tokens along with the call, they will have to pass the address of recipient on the destination chain to which Route tokens will be minted on destination chain.
destChainId: Chain ID of the destination chain in string format.
requestMetadata: Some static information for the request. This is created so that iDapps don’t have to encode it on-chain, they can just send it as a parameter to their iDapp depending on the destination chain Id passed by the user.
requestPacket: This is bytes encoded string consisting of two parameters:
a. destContractAddress: This is the address of the smart contract on the destination chain which will handle the payload that you send from the source chain to the destination chain. 
b. payload: This is bytes containing the payload that you want to send to the destination chain. This can be anything depending on your utility. In this case ,it is the recipient address on destination chain and the amount of tokens to be sent on the destination chain.


Finally, we have generated a cross-chain request that will activate the destination chain contract successfully.


Who will handle our request on the destination chain now that we have sent the request from the source chain?



The function iReceive will be developed to handle the request on the destination chain after the NFT has been burnt on the source chain and a cross-chain transfer request has been generated in the transferCrossChain function.
By handling the request, we imply that the function should be able to decode the encoded data we sent via transferCrossChain, mint the NFT for the receiver on the destination chain.
Keep in mind that the name of the function, iReceive, matters in this case. As this function is called by the Gateway contract on the destination chain, the name and the parameters it gets must correspond for the call to succeed. If the name or the parameters to this function change, the call will fail.

Remember? Initially we implemented an empty function iReceive for the sake of compiling the code at every stage, now is the time to add logic into that function. Make sure you're adding the following logic into that function only and not creating another function named iReceive


code>>>


Let’s check out what each line means;


```sh
function iReceive(
    string memory requestSender,
    bytes memory packet,
    string memory srcChainId
  ) external override returns (bytes memory) {
    require(msg.sender == address(gatewayContract), "only gateway");
    require(
      keccak256(bytes(ourContractOnChains[srcChainId])) ==
        keccak256(bytes(requestSender))
    );

    // decoding our payload
    TransferParams memory transferParams = abi.decode(packet, (TransferParams));
    string memory uri = transferParams.uri;
    safeMint(toAddress(transferParams.recipient), transferParams.nftId,uri);

    return "";
  }
```






```sh
require(msg.sender == address(gatewayContract), "only gateway");
```

Verify that the function's caller is the gateway contract that Router has deployed on the destination chain: This verification ensures that no other smart contract or externally owned account may trigger this function.


```sh
require(
      keccak256(srcContractAddress) ==
        keccak256(ourContractOnChains[srcChainId])
    );
```
Verify that our contract on the destination chain received the request from our contract on the source chain: This verification ensures that only the counterparts of our contracts on various chains can connect with one another and that no other wallets or externally owned accounts are able to interfere with the functioning.


```sh
TransferParams memory transferParams = abi.decode(packet, (TransferParams));
```


Decode the encoded data sent from the source chain: Since the request was generated by us, we know exactly what is received inside it. Since we sent the token ID,recipient address and token URI, we will decode it and store it in a transferParams variable. 

```sh
string memory uri = transferParams.uri;
safeMint(toAddress(transferParams.recipient), transferParams.nftId,uri);

    return "";
  }
	
```


Mint the NFT to recipient: Using the safemint function, we will now mint the NFT that was burned on the source chain to the recipient on the destination chain.
We need to create safeMint function separately for the above purpose

```sh
function safeMint(address to, uint256 tokenId, string memory uri) public 
    {
      // require(msg.sender == owner, "only owner");
        _safeMint(to, tokenId);
        _setTokenURI(tokenId, uri);
    }
```




 safeMint function calls _safeMint function of the ERC-721 contract provided by the Openzeppelin library.


We have now completed the request handling for the destination chain. We must implement the iAck method because we descended from imported libraries or we will encounter an error.
We will only implement an empty function to handle acknowledgement because we don't want to handle it on the source chain.

```sh

 function iAck(
    uint256 requestIdentifier,
    bool execFlag,
    bytes memory execData
  ) external override {}
```


Smart contracts

Here is how your `XERC721.sol` should look like on the chain where we shall do the initial minting, Polygon Mumbai in our case.

```solidity
// SPDX-License-Identifier: Unlicensed
pragma solidity >=0.8.0 <0.9.0;

import "@routerprotocol/evm-gateway-contracts/contracts/IDapp.sol";
import "@routerprotocol/evm-gateway-contracts/contracts/IGateway.sol";
import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

/// @title XERC721
/// @author Yashika Goyal
/// @notice A cross-chain ERC-721 smart contract to demonstrate how one can create
/// cross-chain NFT contracts using Router CrossTalk.
contract XERC721 is ERC721,ERC721URIStorage,IDapp {
  // address of the owner
  address public owner;

  // address of the gateway contract
  IGateway public gatewayContract;

  // chain type + chain id => address of our contract in bytes
  mapping(string => string) public ourContractOnChains;

  // transfer params struct where we specify which NFT should be transferred to
  // the destination chain and to which address
  struct TransferParams {
    uint256 nftId;
    bytes recipient;
    string uri;
  }

  constructor(
    address payable gatewayAddress,
    string memory feePayerAddress
  ) ERC721("ERC721", "ERC721") {
    gatewayContract = IGateway(gatewayAddress);
    owner = msg.sender;

  
    gatewayContract.setDappMetadata(feePayerAddress);
  }

  /// @notice function to set the fee payer address on Router Chain.
  /// @param feePayerAddress address of the fee payer on Router Chain.
  function setDappMetadata(string memory feePayerAddress) external {
    require(msg.sender == owner, "only owner");
    gatewayContract.setDappMetadata(feePayerAddress);
  }

  /// @notice function to set the Router Gateway Contract.
  /// @param gateway address of the gateway contract.
  function setGateway(address gateway) external {
    require(msg.sender == owner, "only owner");
    gatewayContract = IGateway(gateway);
  }

function safeMint(address to, uint256 tokenId, string memory uri) public 
    {
      // require(msg.sender == owner, "only owner");
        _safeMint(to, tokenId);
        _setTokenURI(tokenId, uri);
    }
     function tokenURI(uint256 tokenId)
        public
        view
        override(ERC721, ERC721URIStorage)
        returns (string memory)
    {
        return super.tokenURI(tokenId);
    }
  function mint(address to, uint256 tokenId,string memory uri) external {
    require(msg.sender == owner, "only owner");
        _safeMint(to, tokenId);
        _setTokenURI(tokenId, uri);
  }

  /// @notice function to set the address of our ERC20 contracts on different chains.
  /// This will help in access control when a cross-chain request is received.
  /// @param chainId chain Id of the destination chain in string.
  /// @param contractAddress address of the ERC20 contract on the destination chain.
  function setContractOnChain(
    string calldata chainId,
    string calldata contractAddress
  ) external {
    require(msg.sender == owner, "only owner");
    ourContractOnChains[chainId] = contractAddress;
  }
 function _burn(uint256 tokenId) internal override(ERC721, ERC721URIStorage) {
        super._burn(tokenId);
    }
  /// @notice function to generate a cross-chain NFT transfer request.
  /// @param destChainId chain ID of the destination chain in string.
  /// @param transferParams transfer params struct.
  /// @param requestMetadata abi-encoded metadata according to source and destination chains
  function transferCrossChain(
    string calldata destChainId,
    TransferParams calldata transferParams,
    bytes calldata requestMetadata
  ) public payable {
    require(
      keccak256(bytes(ourContractOnChains[destChainId])) !=
        keccak256(bytes("")),
      "contract on dest not set"
    );

    require(
      _ownerOf(transferParams.nftId) == msg.sender,
      "caller is not the owner"
    );

    // burning the NFT from the address of the user calling _burn function
    _burn(transferParams.nftId);

    // sending the transfer params struct to the destination chain as payload.
    bytes memory packet = abi.encode(transferParams);
    bytes memory requestPacket = abi.encode(
      ourContractOnChains[destChainId],
      packet
    );

    gatewayContract.iSend{ value: msg.value }(
      1,
      0,
      string(""),
      destChainId,
      requestMetadata,
      requestPacket
    );
  }

  /// @notice function to get the request metadata to be used while initiating cross-chain request
  /// @return requestMetadata abi-encoded metadata according to source and destination chains
  function getRequestMetadata(
    uint64 destGasLimit,
    uint64 destGasPrice,
    uint64 ackGasLimit,
    uint64 ackGasPrice,
    uint128 relayerFees,
    uint8 ackType,
    bool isReadCall,
    string calldata asmAddress
  ) public pure returns (bytes memory) {
    bytes memory requestMetadata = abi.encodePacked(
      destGasLimit,
      destGasPrice,
      ackGasLimit,
      ackGasPrice,
      relayerFees,
      ackType,
      isReadCall,
      asmAddress
    );
    return requestMetadata;
  }

  /// @notice function to handle the cross-chain request received from some other chain.
  /// @param requestSender address of the contract on source chain that initiated the request.
  /// @param packet the payload sent by the source chain contract when the request was created.
  /// @param srcChainId chain ID of the source chain in string.
  function iReceive(
    string memory requestSender,
    bytes memory packet,
    string memory srcChainId
  ) external override returns (bytes memory) {
    require(msg.sender == address(gatewayContract), "only gateway");
    require(
      keccak256(bytes(ourContractOnChains[srcChainId])) ==
        keccak256(bytes(requestSender))
    );

    // decoding our payload
    TransferParams memory transferParams = abi.decode(packet, (TransferParams));
    string memory uri = transferParams.uri;
    safeMint(toAddress(transferParams.recipient), transferParams.nftId,uri);

    return "";
  }

  /// @notice function to handle the acknowledgement received from the destination chain
  /// back on the source chain.
  /// @param requestIdentifier event nonce which is received when we create a cross-chain request
  /// We can use it to keep a mapping of which nonces have been executed and which did not.
  /// @param execFlag a boolean value suggesting whether the call was successfully
  /// executed on the destination chain.
  /// @param execData returning the data returned from the handleRequestFromSource
  /// function of the destination chain.
  function iAck(
    uint256 requestIdentifier,
    bool execFlag,
    bytes memory execData
  ) external override {}

  /// @notice Function to convert bytes to address
  /// @param _bytes bytes to be converted
  /// @return addr address pertaining to the bytes
  function toAddress(bytes memory _bytes) internal pure returns (address addr) {
    bytes20 srcTokenAddress;
    assembly {
      srcTokenAddress := mload(add(_bytes, 0x20))
    }
    addr = address(srcTokenAddress);
  }
}

```

We will be using the same contract for the destination contract as well ,so no need of writing the contract again for the destination chain.

Congratulations for completing the contracts for your cross-chain NFTs!


As you're now ready to build cross-chain contracts using Router's Crosstalk Utils, your challenge is to create a similar cross-chain NFT, named as `XERC1155.sol`, build upon ERC1155 standard.



```// SPDX-License-Identifier: Unlicensed
pragma solidity >=0.8.0 <0.9.0;

import "@routerprotocol/evm-gateway-contracts/contracts/IDapp.sol";
import "@routerprotocol/evm-gateway-contracts/contracts/IGateway.sol";
import "@openzeppelin/contracts/token/ERC1155/ERC1155.sol";

/// @title XERC1155
/// @author Yashika Goyal
/// @notice A cross-chain ERC-1155 smart contract to demonstrate how one can create
/// cross-chain NFT contracts using Router CrossTalk.
contract XERC1155 is ERC1155, IDapp {
  // address of the owner
  address public owner;

  // address of the gateway contract
  IGateway public gatewayContract;

  // chain type + chain id => address of our contract in bytes
  mapping(string => string) public ourContractOnChains;

  // transfer params struct where we specify which NFTs should be transferred to
  // the destination chain and to which address
  struct TransferParams {
    uint256[] nftIds;
    uint256[] nftAmounts;
    bytes nftData;
    bytes recipient;
  }

  constructor(
    string memory _uri,
    address payable gatewayAddress,
    string memory feePayerAddress
  ) ERC1155(_uri) {
    gatewayContract = IGateway(gatewayAddress);
    owner = msg.sender;

    // minting ourselves some NFTs so that we can test out the contracts
    _mint(msg.sender, 1, 10, "");

    gatewayContract.setDappMetadata(feePayerAddress);
  }

  /// @notice function to set the fee payer address on Router Chain.
  /// @param feePayerAddress address of the fee payer on Router Chain.
  function setDappMetadata(string memory feePayerAddress) external {
    require(msg.sender == owner, "only owner");
    gatewayContract.setDappMetadata(feePayerAddress);
  }

  /// @notice function to set the Router Gateway Contract.
  /// @param gateway address of the gateway contract.
  function setGateway(address gateway) external {
    require(msg.sender == owner, "only owner");
    gatewayContract = IGateway(gateway);
  }

  function mint(
    address account,
    uint256[] memory nftIds,
    uint256[] memory amounts,
    bytes memory nftData
  ) external {
    require(msg.sender == owner, "only owner");
    _mintBatch(account, nftIds, amounts, nftData);
  }

  /// @notice function to set the address of our NFT contracts on different chains.
  /// This will help in access control when a cross-chain request is received.
  /// @param chainId chain Id of the destination chain in string.
  /// @param contractAddress address of the NFT contract on the destination chain.
  function setContractOnChain(
    string calldata chainId,
    string calldata contractAddress
  ) external {
    require(msg.sender == owner, "only owner");
    ourContractOnChains[chainId] = contractAddress;
  }

  /// @notice function to generate a cross-chain NFT transfer request.
  /// @param destChainId chain ID of the destination chain in string.
  /// @param transferParams transfer params struct.
  /// @param requestMetadata abi-encoded metadata according to source and destination chains
  function transferCrossChain(
    string memory destChainId,
    TransferParams memory transferParams,
    bytes memory requestMetadata
  ) public payable {
    require(
      keccak256(bytes(ourContractOnChains[destChainId])) !=
        keccak256(bytes("")),
      "contract on dest not set"
    );

    // burning the NFTs from the address of the user calling _burnBatch function
    _burnBatch(msg.sender, transferParams.nftIds, transferParams.nftAmounts);

    // sending the transfer params struct to the destination chain as payload.
    bytes memory packet = abi.encode(transferParams);
    bytes memory requestPacket = abi.encode(
      ourContractOnChains[destChainId],
      packet
    );

    gatewayContract.iSend{ value: msg.value }(
      1,
      0,
      string(""),
      destChainId,
      requestMetadata,
      requestPacket
    );
  }

  /// @notice function to get the request metadata to be used while initiating cross-chain request
  /// @return requestMetadata abi-encoded metadata according to source and destination chains
  function getRequestMetadata(
    uint64 destGasLimit,
    uint64 destGasPrice,
    uint64 ackGasLimit,
    uint64 ackGasPrice,
    uint128 relayerFees,
    uint8 ackType,
    bool isReadCall,
    bytes memory asmAddress
  ) public pure returns (bytes memory) {
    bytes memory requestMetadata = abi.encodePacked(
      destGasLimit,
      destGasPrice,
      ackGasLimit,
      ackGasPrice,
      relayerFees,
      ackType,
      isReadCall,
      asmAddress
    );
    return requestMetadata;
  }

  /// @notice function to handle the cross-chain request received from some other chain.
  /// @param requestSender address of the contract on source chain that initiated the request.
  /// @param packet the payload sent by the source chain contract when the request was created.
  /// @param srcChainId chain ID of the source chain in string.
  function iReceive(
    string calldata requestSender,
    bytes calldata packet,
    string calldata srcChainId
  ) external override returns (bytes memory) {
    require(msg.sender == address(gatewayContract), "only gateway");
    require(
      keccak256(bytes(ourContractOnChains[srcChainId])) ==
        keccak256(bytes(requestSender))
    );

    // decoding our payload
    TransferParams memory transferParams = abi.decode(packet, (TransferParams));
    _mintBatch(
      toAddress(transferParams.recipient),
      transferParams.nftIds,
      transferParams.nftAmounts,
      transferParams.nftData
    );

    return "";
  }

  /// @notice function to handle the acknowledgement received from the destination chain
  /// back on the source chain.
  /// @param requestIdentifier event nonce which is received when we create a cross-chain request
  /// We can use it to keep a mapping of which nonces have been executed and which did not.
  /// @param execFlag a boolean value suggesting whether the call was successfully
  /// executed on the destination chain.
  /// @param execData returning the data returned from the handleRequestFromSource
  /// function of the destination chain.
  function iAck(
    uint256 requestIdentifier,
    bool execFlag,
    bytes memory execData
  ) external override {}

  /// @notice Function to convert bytes to address
  /// @param _bytes bytes to be converted
  /// @return addr address pertaining to the bytes
  function toAddress(bytes memory _bytes) internal pure returns (address addr) {
    bytes20 srcTokenAddress;
    assembly {
      srcTokenAddress := mload(add(_bytes, 0x20))
    }
    addr = address(srcTokenAddress);
  }
}
```







**Deployment**

Now, we will start deployment;

Compile your XERC721.sol contract using the Solidity Compiler.


After successful compilation, go to deploy and run Transactions window Select Injected Provider - Metamask under Environment and connect your metamask to Polygon Mumbai network.



Deploy the contract XERC721.sol in which we were passing the Constructor arguments: your NFT's name and symbol, the feePayer Address, and the gateway address for the Polygon Mumbai testnet. The gateway contracts' addresses can be found here.Confirm the transaction that appears on metamask after you transact.



Go to the Deploy and run transactions window and connect your metamask to the Avalanche Fuji network .


Deploy the contract similarly by passing the constructor arguments in the similar manner we did for the contract on Mumbai. Make sure to pass the gateway address for Fuji testnet here.




And the deployment of our contracts is complete. If you scroll down through the DEPLOY AND RUN TRANSACTIONS Tab, you can see instances of your deployed contracts that look like this. 

It’s time to mint your NFT on the source chain !!
1. Connect your Metamask to Mumbai Network
2. Go to Deployed Contracts and choose the first  instance
3. Go to the mint function and pass in the address you wanted the NFT to get minted to, Id you want the NFT  to have and the URI for your NFT.

Here's news, you can also see your NFTs that you minted to yourself on Polygon Mumbai.By utilising the ownerOf function, you may determine who owns the token IDs .
Your address must appear in the output, according to this.


Then we also need to set the destination contract on the source chain and via versa.

Connect the Polygon Mumbai network with your metamask.
Make sure you've opened the first under Deployed contracts in Remix in the manner described above. You can access all the functions we created and those our contract has inherited from other contracts here.


Transact by providing the Chain ID's, and address of the contract that we deployed on the Fuji network to the setContractOnChain function
Put 43113 as the chain Id, and the address of the  contract that we deployed on Fuji.




Connect your metamask to the Avalanche Fuji network after this step.
Ensure that the contract we deployed on Avalanche Fuji is open in Remix under Deployed contracts.
Transact by supplying the chain ID, and address of the contract that we placed on the Mumbai network to the setContractOnChain function. As an example, enter 80001 as the chain ID, and the address of the contract that was set up in Mumbai. 




Now we will test our Cross chain NFT Smart contracts.
We can finally see the results of our contract now. 

Follow the steps;

Connect your metamask to Polygon Mumbai network.


Make sure you have opened the contract that we deployed on Polygon Mumbai under Deployed contracts in Remix.


Get the requestMetadata by passing necessary parameters in getRequestMetadata function as discussed earlier.



Transact by passing the  chain Id, transferParams and requestMetadata to the transferCrossChain function .
Since, tranferParams is a struct 

```
struct TransferParams {
    uint256 nftId;
    bytes recipient;
    string uri;
  }
```
We need to pass in this format :-
[<nftId>,<recipient address>,<uri>]
	
Visit Router Explorer and click on Fee Payer option present in More section.Connect your metamask to Router Testnet .Find your dapp address there and click on approve button corresponding to your dapp to approve it.



Once, the approval is done, go to CROSSCHAIN . You can track the status of your transaction there. Wait for sometime till your transaction gets executed.



Go to your Mumbai instance in Remix and call the function ownerOf like we did before while your metamask is still attached to Polygon Mumbai. Verify who the owner of the NFT you just sent through transferCrossChain function. Your address wouldn't be in the output, though. It indicates your NFT was indeed burnt in Mumbai and is on its way to you on Fuji.


Now, connect the Avalanche Fuji network using your metamask, access your Fuji instance, and use the same procedure as before to use the ownerOf method. Verify who the owner of the NFT you just sent through transferCrossChain function from the Mumbai instance of the contract.Your address needs to appear in the output, which you can see. It indicates that you have received your burnt NFT from Mumbai on Fuji.
