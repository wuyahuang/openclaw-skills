---
name: soon-network-explorer
description: Query Soon Network account balances, transaction history, and token-specific transfers.
homepage: https://soon-network-explorer-production.up.railway.app
metadata: {"clawdbot":{"emoji":"🪙","requires":{"bins":["curl"]}}}
---

# Soon Network Explorer

Query Soon Network account info via HTTP endpoints. No API key required.

## Query Balance

Quick one-liner:
```bash
curl -s "https://soon-network-explorer-production.up.railway.app/account/balance?address=<address>"
# Output: {"ETH":0.1,"USDT":1,"USDC":1}
```
Example Response:
```
Address: <address>

💰 Balances:

* ETH : 1
* USDT: 1
* USDC: 1

[View Account](https://explorer.soo.network/address/<address>)
```

## Query Transaction History

Quick one-liner:
```bash
curl -s "https://soon-network-explorer-production.up.railway.app/account/history?address=<address>&limit=5"
# Output: {"history":[{"date":"2026-02-26 00:50:10 (UTC)","viewTx":"[View Tx](https://explorer.soo.network/tx/)"}]}
```
Returns a list of transactions with timestamp and clickable transaction link in Markdown.

Example Response:
```
Address: 7FFiaNrQSaH7RnBuvNWkDZBeMZ9cHv36c2pdnd2eQnH2

⏰ Recent Transfers:
* 2026-02-26 00:50:10 (UTC) | [View Tx](https://explorer.soo.network/tx/)
* 2026-02-26 00:50:10 (UTC) | [View Tx](https://explorer.soo.network/tx/)
```

## Query Token-specific Transfer History

Quick one-liner:
```bash
curl -s "https://soon-network-explorer-production.up.railway.app/account/transfer_history_by_token_symbol?address=<address>&symbol=USDT&limit=5"
# Output: [{"date":"2026-02-26 00:50:10 (UTC)","token":"USDT","amount":"1","direction":"OUT","viewTx":"[View Tx](https://explorer.soo.network/tx/)"}]
```
Returns a list of token transfers with timestamp, amount, direction (IN/OUT), and transaction link.

Example Response:
```
Address: 7FFiaNrQSaH7RnBuvNWkDZBeMZ9cHv36c2pdnd2eQnH2

⏰ Recent USDT Transfers:
* 2026-02-26 00:50:10 (UTC) | OUT | 4.99 | [View Tx](https://explorer.soo.network/tx/)
* 2026-02-26 00:50:10 (UTC) | IN  | 4.99 | [View Tx](https://explorer.soo.network/tx/)
```

## Usage Notes
*	<ADDRESS> must be a Soon Network address (32~44 chars).
*	<SYMBOL> is the token symbol, e.g., USDT, ETH, USDC.
*	viewTx links are Markdown-ready and clickable.
*	All endpoints return JSON and are ready for programmatic use or curl testing.