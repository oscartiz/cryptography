# cryptography

Jupyter notebooks implementing zero-knowledge proof systems and cryptographic primitives **from scratch** — the goal is pedagogical, not production. Every protocol is built up from finite-field arithmetic, elliptic-curve operations, and pairings on BN128, so you can read each cell and see exactly what's being computed.

## Contents

| Path | Topic |
|---|---|
| [`Groth16/Groth16.ipynb`](./Groth16/Groth16.ipynb) | A full Groth16 SNARK pipeline: arithmetic circuit → R1CS → QAP → trusted setup → prover → verifier, with the pairing check `e(A, B) = e(α, β) · e(L, γ) · e(C, δ)` evaluated explicitly. |
| [`Plonk/plonk.ipynb`](./Plonk/plonk.ipynb) | Step-by-step PLONK construction: arithmetization, copy constraints via permutation argument, polynomial commitments, and the final check. |
| [`Plonk/zk_plonk.ipynb`](./Plonk/zk_plonk.ipynb) | A more complete (zk-)PLONK implementation with blinding factors, Fiat–Shamir transform, and a working end-to-end proof/verify cycle. |
| [`PLONKVis/visualized.ipynb`](./PLONKVis/visualized.ipynb) | Visualization scratchpad for PLONK polynomials and constraint tables. |
| [`mastering_ethereum_zkp.ipynb`](./mastering_ethereum_zkp.ipynb) | Walkthrough following the ZKP material from *Mastering Ethereum* — hashing, commitments, basic Σ-protocols. |
| [`sinsemilla.ipynb`](./sinsemilla.ipynb) | Sinsemilla hash (the Pasta-curve-friendly hash used by Zcash/Halo 2). |

## Stack

The notebooks share a small dependency set:

- [`galois`](https://github.com/mhostetter/galois) — finite-field arithmetic over arbitrary prime fields (used heavily for Lagrange interpolation, polynomial division, and zero/vanishing polynomials).
- [`py_ecc`](https://github.com/ethereum/py_ecc) — BN128 group operations and pairings (`G1`, `G2`, `pairing`, `final_exponentiate`).
- `numpy`, `hashlib`, `secrets` — utilities.

## Running

```bash
pip install galois py_ecc numpy jupyterlab
jupyter lab
```

Open any notebook; cells are ordered to be run top-to-bottom.

## Why this exists

Reading a ZK paper and reading a 10k-LOC Rust prover are very different exercises. These notebooks aim for the middle ground: enough working code to actually generate and verify a proof, but small enough that every operation is inspectable in a REPL.
