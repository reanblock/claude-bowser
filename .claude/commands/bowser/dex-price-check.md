---
description: Check token price across 3 pools on different chains via dexscreener and report arbitrage
argument-hint: <token>
defaults:
  skill: playwright-bowser
  mode: headed
---

# DEX Price Checker

Check the current price of {PROMPT} across 3 pools on different chains using dexscreener.com.

## Workflow

1. Navigate to `https://dexscreener.com/search?q={PROMPT}`
2. Wait for results to load (look for a list of trading pairs)
3. Find 3 pools for {PROMPT}/USD (or a stablecoin pair: USDC, USDT, DAI) each on a **different chain** (e.g. Ethereum, Arbitrum, Base, BSC, Polygon, Solana)
4. For each pool, record:
   - Pool name and DEX (e.g. Uniswap, Curve, Camelot)
   - Chain
   - Current price in USD
   - Pool address (if visible)
5. Calculate the **average price** across the 3 pools
6. Identify **arbitrage opportunities**: flag any pool where the price deviates >0.3% from the average, and calculate the spread %
7. Report results in this format:

| Pool | DEX | Chain | Price (USD) | Deviation |
|------|-----|-------|-------------|-----------|
| ...  | ... | ...   | ...         | ...       |

- **Average Price**: $X.XX
- **Arbitrage Opportunities**: list any pools with >0.3% spread, or "None found"
