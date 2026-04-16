# Retrieval Optimization: From Tokenization to Vector Quantization

> **Course:** [DeepLearning.AI](https://www.deeplearning.ai/short-courses/retrieval-optimization-from-tokenization-to-vector-quantization/) × [Qdrant](https://qdrant.tech/)  
The course covers the internals of embedding models and retrieval pipelines, from how text gets tokenized all the way through to vector quantization — key knowledge for building and optimizing RAG applications at scale.

---

## Code Outline
 
### 1. Introduction
 
A high-level overview of the course goals and why retrieval optimization matters in RAG systems. Sets up the two main pillars: understanding *how* text becomes vectors (tokenization + embeddings), and *how* to make vector search faster and more accurate (HNSW + quantization).
 
---
 
### 2. Embedding Models
 
Covers the internals of embedding models and how raw text is transformed into dense vector representations. Key topics:
 
- How encoder-based models (e.g., sentence-transformers) produce embeddings
- The role of pooling strategies (mean pooling, CLS token)
- Why the choice of embedding model fundamentally shapes search quality
---
 
### 3. Role of the Tokenizers
 
Explores what happens *before* the model sees your text. Key topics:
 
- How tokenizers split text into subword units
- Training methods: **Byte-Pair Encoding (BPE)**, **WordPiece**, **Unigram**, and **SentencePiece**
- Why tokenizer design directly affects what the model "understands"
---
 
### 4. Practical Implications of Tokenization
 
Bridges theory and real-world pitfalls. Key topics:
 
- **Unknown tokens** and out-of-vocabulary issues
- **Domain-specific identifiers** (product codes, medical terms, etc.) that tokenizers handle poorly
- **Numerical values** and how tokenization fragments them
- Strategies to mitigate tokenizer-induced search quality degradation
---
 
### 5. Measuring Search Relevance
 
Before optimizing, you need to measure. Key topics:
 
- Standard retrieval quality metrics: **Precision@K**, **Recall@K**, **MRR**, **NDCG**
- How to build evaluation datasets for your domain
- Using Qdrant to benchmark retrieval quality in practice
---
 
### 6. Optimizing HNSW Search
 
Most vector databases use **Hierarchical Navigable Small World (HNSW)** graphs for approximate nearest-neighbor search. Key topics:
 
- How HNSW builds and traverses its graph structure
- Key parameters: `m` (connections per node) and `ef_construction` / `ef` (search beam width)
- Speed vs. recall trade-offs and how to tune them for your use case
---
 
### 7. Vector Quantization
 
Quantization compresses vectors to reduce memory footprint and speed up search. Key topics:
 
- **Scalar Quantization (SQ):** reduces float32 → int8, ~4× memory reduction
- **Product Quantization (PQ):** splits vectors into subspaces, large memory savings with tunable accuracy loss
- **Binary Quantization (BQ):** most aggressive compression, vectors become bit strings — works well with high-dimensional models
- Impact of each method on memory requirements, search speed, and recall quality

---

## Key Takeaways

| Topic | Key Insight |
|---|---|
| Tokenization | Mismatched tokenizers silently degrade search quality — always validate on your domain's vocabulary |
| Embeddings | Model choice + pooling strategy matters more than index tuning for baseline quality |
| Evaluation | Can't optimize what you don't measure — build a domain-specific eval set early |
| HNSW | Higher `m` and `ef` → better recall but slower indexing/search; tune for your latency budget |
| Quantization | Binary quantization offers the best speed gains but requires high-dimensional models (1000+ dims) |

---

## Resources

- 📖 [Course page](https://www.deeplearning.ai/short-courses/retrieval-optimization-from-tokenization-to-vector-quantization/)
- 📦 [Qdrant docs](https://qdrant.tech/documentation/)
- 🤗 [Sentence Transformers](https://www.sbert.net/)
- 🔢 [Tokenizer playground](https://huggingface.co/tokenizer-playground)
