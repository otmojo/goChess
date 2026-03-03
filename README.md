# goChess


GoChess の開発過程において、状態永続化の仕組みを根本から理解するため、
LSM-tree / Bitcask アーキテクチャをベースにした極小構成の KV ストレージエンジンを自作しました。https://github.com/otmojo/mini-kv

当初は Redis を用いて対局状態を管理していましたが、
外部ストレージに依存せずに、棋局の FEN 状態を直接ディスクへ永続化する仕組みを実装することで、

* クラッシュリカバリの挙動
* 書き込み増幅（Write Amplification）
* Append-only ログ設計
* コンパクション戦略

といったストレージ内部構造の理解を目的としています。

この mini-kv を将来的に Redis の代替として利用し、
GoChess の対局状態を管理することを想定しています。

---



During the development of GoChess, I built a minimal LSM-tree/Bitcask-inspired key-value storage engine (https://github.com/otmojo/mini-kv) from scratch to deeply understand state persistence mechanisms.

Instead of relying solely on Redis, I experimented with persisting chess game FEN states directly to disk using my own storage engine. The goal was to explore:

* Crash recovery behavior
* Write amplification characteristics
* Append-only log design
* Compaction strategies

The intention is to potentially replace Redis for game state storage and gain hands-on experience with low-level storage engine internals.

