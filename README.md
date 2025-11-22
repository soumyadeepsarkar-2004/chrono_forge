# Chrono Forge

Dynamic, evolvable NFTs powered by on‑chain SVG rendering and interactive lifecycle mechanics. Runs on the Avalanche Fuji testnet (no real AVAX required).

Live Demo: (attached above)

> NFTs (Aetherium Shards) evolve through daily energizing, trait infusion, cleansing, and multi‑generational forging.

## ✨ Core Features

### Evolution & State
- Dynamic NFT evolution: Aetherium Shards transform based on user actions
- On-chain SVG artwork: Generated directly in the smart contract; updates as attributes change
- Evolving attributes: Energy, Purity, Core Element, Generation, Infused Traits
- Generational forging: Combine evolved NFTs to mint higher‑generation specimens

### User Actions
- 🔥 Mint: Acquire your first Aetherium Shard
- ⚡ Energize (daily): Increases Energy; streak bonuses reward consistency
- 🧬 Infuse: Burn partner tokens (future integrations) to add unique traits
- 🐉 Evolve: Advance the form once thresholds are met
- 🛠 Forge: Merge two qualified NFTs for a next‑generation shard
- 🌊 Cleanse: Remove unwanted traits to improve Purity

### Systems
- Daily streak logic for energizing
- Trait purity vs infused ability balance
- Fully reactive UI reflecting on-chain state

## 🧊 Avalanche Fuji Testnet

- Fast confirmations / low fees
- EVM compatible (Solidity + existing tooling)
- Free test AVAX via faucets

Get test AVAX:
1. Visit https://faucet.avax.network/
2. Select Fuji / enter wallet / request funds

## 🛠 Tech Stack

### Smart Contracts
- Solidity
- Hardhat
- OpenZeppelin libraries
- (Configured for Avalanche Fuji)

### Frontend
- Next.js 15 (App Router)
- TypeScript
- Wagmi + Viem (wallet & chain interaction)
- Tailwind CSS + utility layering
- Radix UI primitives
- React Query (@tanstack/react-query) for data/state
- WalletConnect (optional, via Project ID)

## 📂 Suggested Project Structure (abridged)
- contracts/ Core NFT + trait/evolution logic
- scripts/ Deployment & maintenance (deploy.ts, etc.)
- app/ Next.js route handlers & UI
- components/ Reusable UI modules
- lib/ Chain config, wagmi client, helpers
- hooks/ Custom React hooks (query + evolution logic)

(Adjust based on actual repo layout.)

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- npm or yarn
- Git
- MetaMask (or compatible wallet)

### 1. Clone & Install
```bash
git clone https://github.com/soumyadeepsarkar-2004/chrono_forge.git
cd chrono_forge
npm install
```

### 2. Environment Setup
Copy example file:
```bash
cp .env.example .env.local
```

Add/update values (example list; adjust to what the project actually uses):
```
NEXT_PUBLIC_CONTRACT_ADDRESS=0xYourDeployedContract
NEXT_PUBLIC_RPC_URL=https://api.avax-test.network/ext/bc/C/rpc
NEXT_PUBLIC_WALLETCONNECT_PROJECT_ID=your_project_id   # optional
NEXT_PUBLIC_CHAIN_ID=43113
```

### 3. Deploy Contracts (Avalanche Fuji)
```bash
npx hardhat run scripts/deploy.ts --network avalancheFuji
```
Then update `NEXT_PUBLIC_CONTRACT_ADDRESS` in `.env.local`.

### 4. Run Dev Server
```bash
npm run dev
```
Visit http://localhost:3000 and connect wallet.

### 5. Mint & Interact
- Mint an Aetherium Shard
- Energize daily to raise Energy
- Infuse traits (future integrations)
- Forge/evolve when thresholds met

## 🔄 Updating Artwork
Because SVG is generated on-chain, any attribute change (energy, purity, traits, generation) triggers a fresh tokenURI render—no off-chain metadata refresh required.

## ⚙️ Contract Interaction (Example viem/wagmi snippet)
```ts
// pseudo example
const { writeContract } = useWriteContract();
writeContract({
  address: CONTRACT_ADDRESS,
  abi: chronoForgeAbi,
  functionName: 'energize',
  args: [tokenId],
});
```

## 🧪 Testing (if implemented)
```bash
npx hardhat test
```
Add tests under `test/` to cover:
- Minting rules
- Energize cooldown/streak
- Trait infusion / cleanse logic
- Generation forging constraints

## 🛡 Security & Integrity
- OpenZeppelin base inheritance for ERC721
- Purity system prevents uncontrolled trait accumulation
- Controlled forging ensures rarity escalation
- Recommend adding access-control & pausable features if not already present

## 🧭 Roadmap (Suggested)
- Partner token integration for infusion
- Achievement / streak badges
- Marketplace metadata sync / indexer script
- Cross-chain expansion (if desired)
- In-contract rarity scoring

## 🧩 Troubleshooting

### WalletConnect WebSocket Errors
Messages like “Fatal socket error received, closing transport”:
- Typically transient testnet/WebSocket issues
- App still works with injected wallets (MetaMask)
- Provide a valid Project ID to stabilize

### Missing Contract Address
- UI will fail to read NFT state
- Ensure deployment succeeded and address copied correctly

### RPC Instability
- Switch to a reliable Avalanche Fuji RPC endpoint
- Clear wallet network cache

## 📚 Learn More
- Avalanche Docs: https://docs.avax.network/
- Hardhat: https://hardhat.org/
- Wagmi: https://wagmi.sh/
- Viem: https://viem.sh/
- OpenZeppelin: https://docs.openzeppelin.com/

## 🌐 Deployment
To deploy frontend (example with Vercel):
```bash
npm run build
vercel --prod
```
Ensure production `.env` has the same contract address and chain configuration.

## 🤝 Attribution
Fork of original project: https://github.com/Aritra203/chrono_forge  
Enhanced for Avalanche Fuji testnet usage.

## ⚠ Disclaimer
Chrono Forge currently operates on a test network. Tokens/NFTs have no real-world monetary value. Use only test AVAX.

## 📄 License
(If a license exists in the original upstream repo, add it here. Otherwise consider adding MIT/Apache-2.0.)