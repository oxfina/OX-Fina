# "OX Token" Smart Contract

## Specification:

1. ./docs/OX\_Fina.pdf pp 1-7
2. Discussion/chat with Ravi Kash via Moneo platform

## Warnings

1. The contract enables any Ethereum address to send Ether and be the recipient
   of tokens either directly or by transfer. Each user must understand they are
   responsible for ensuring the accuracy of target addresses and for ensuring
   anything sent to that address is retrievable.

2. The client will be the owner of the contract and will have the ability to
   shutdown the contract and render it inoperative.

3. The extra 30% will only be allocated after the sale is over and someone
   calls expand() or does any transfer().

4. Ethereum events will be published to indicate sales ("Receipt" events) and
   transfers ("Transfer" events). These events will be stored in the Ethereum
   logs forever and will be viewable by anyone knowing the smart contract
   address (SCA).

5. Ether can be sent to the contract by anyone at anytime for any reason. It
   can be withdrawn only by the contract owner. This is all separate from the
   purchase of tokens. There is no limit on the amount of Ether that can be
   stored, but clients are advised to mitigate technology/platform risks by
   moving funds to safe locations and ensuring no single account contains more
   Ether than one is prepared to risk.

6. Client is advised to obtain an independent review of the code, tests and
   results prior to placing any financial trust in these works.

## Test Scope

 0. Smart contract has correct initial values when created
 1. Anyone can send Ether to the smart contract address
 2. Only the contract owner can withdraw Ether
 3. The owner cannot withdraw more than the full balance of Ether
 4. Full Ether balance goes to owner if contract is shut down
 5. Only the owner can shut down the contract
 6. Token sales cannot begin before the start time
 7. Token sales cannot happen after the sale ends
 8. Can sell (700,000,000 / 1.25) on day one
 9. Can sell (700,000,000 / 1.2) after day one but within week one
10. Can sell (700,000,000 / 1.15) in week two
11. Can sell (700,000,000 / 1.10) in week three
12. Can sell (700,000,000 / 1.05) in week four
13. Can sell 700,000,000 after week four but before one month
14. Enforces 700,000,000 limit correctly
15. No holder can transfer before sale ends
16. Bounty is calculated correctly when sale ends
17. Holder can transfer up to full holding
18. Holder cannot transfer more than full holding
19. Transfers do not work after closedown
20. Only the contract owner can transfer ownership

## Test Notes

1. All tests employed 'testrpc' without arguments, except for test #14 which
   needed a large account balance to complete its test.

2. Temporary changes were made to the solidity contract to enable testing.
   These were commented out in the version compiled for production.

## Test Code

See the ./tests/ subdirectory. Each script is numbered according to the list
above.

## Test Report

The shell session is captured in ./tests/results.txt

Note that the results file contains a recorded terminal session. If one opens
it with a text editor one will see all the color output escape sequences making
it difficult to read.

Simply open a color xterm and do '$ cat results.txt' and color will work.

