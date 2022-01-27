# 経歴 / Credentials

* 2008/04 -- 2013/03. 学士 [筑波大学情報学群](https://inf.tsukuba.ac.jp/)
* 2013/04 -- 2015/03. 修士 [筑波大学システム情報工学研究科](https://www.sie.tsukuba.ac.jp/)
* 2015/04 -- 2018/03. 博士（工学） 筑波大学システム情報工学研究科
    * 博士論文: Timed Pushdown Automata: Expressiveness and Reachability
        * 邦題: 時間プッシュダウンオートマトンの表現力と到達可能性問題
    * URL: https://doi.org/10.15068/00152389
* 2015/04--2018/03. JSPS 学振特別研究員 DC1 [研究プロジェクトページ](https://research-er.jp/projects/view/923384)
* 2018/04--（現在): 株式会社ドワンゴ
    * 分散オブジェクトストレージ[Frugalos](https://github.com/frugalos/frugalos)の基礎研究と開発に従事
    * Keywords: Erasure Coding, Persistent Key-value Storage, Raft, MultiPaxos, Paxos

# スキル / My Skills

## 計算機科学の理論に関して
* プログラム理論 / Theory of Program(ming)
* オートマトン理論、形式言語理論 / Automata Theory, Formal Language Theory
* ソフトウェア検証、プログラム検証 / Software Verification, Program Verification
* プログラミングや検証のための論理 / Computational Logic
* 定理証明系、定理証明支援系 / Proof Assistant(Coq, Agda2, Isabelle/HOL, etc.)
* 分散計算、分散システムを支える理論 / Theory & Methods for Distributed Computing and Systems.

それぞれのトピックに対応する論文も筆頭著者で出版しています。"主な論文"のセクションをご覧ください。

## プログラミングに関して
* Linuxカーネルプログラミング
    * 高効率DBの実現を支えるファイルシステムの実装をしました https://github.com/yuezato/minfs
* 習熟しているプログラミング言語
  * C, C++, Rust, OCaml, Haskell, Coq
      * Cに関しては「安全なC言語の処理系」を作る産総研(AIST)のプロジェクト FailSafeC をお手伝いしていました
          * https://staff.aist.go.jp/y.oiwa/FailSafeC/
          * 処理系はOCamlで書かれています
      * Rustに関しては十万行スケールの分散オブジェクトストレージのOSS開発に主メンバとして携わっています
          * https://github.com/frugalos/frugalos
      * また、以下に記述する論文の実証ライブラリの実現にもRustを用いています
          * https://github.com/yuezato/xorslp_ec
      * Coqではこれに関する論文を一編出版しています http://id.nii.ac.jp/1001/00081612/

# 現在の興味 / Topics of my interest

* 大規模計算・システムを実現するためのプログラミング技術・証明
    * Storage technology: Erasure coding, Optimized File system for specific devices
    * Distributed Algorithms
    * Space-efficient Data structures
* 機械学習で使われる統計や幾何的手法を用いた新たな（ノンスタンダードな）プログラム解析
    * プログラムの解析や検証に学習（≠ 深層学習）を使う方法はかなり浸透してきていると言えます: https://www.usenix.org/conference/osdi21/presentation/yao
    * こうしたひとまず適用してみるの段階を超え、「なぜうまく行くのか・どういった構造がプログラムに隠されていたのか」を
    機械学習の数学的基盤をもとに明らかにする、次のステップに興味があります。
* プログラムの安全性に立脚するソフトウェアやシステムの安全性検証
    * あいまいなcriteriaに訴える安全性検証を排し、安全か否かをエンジニアリングや計算の問題を介して形式化し、数理的に取り組むことに興味があります。
    * 他の人の仕事ですが一例です: https://arxiv.org/abs/2010.12450, https://doi.org/10.11309/jssst.38.2_53
        * これらはオートマトンの理論を用いてDoSに関する脅威を検証するお話です

## 興味に関連する自分のリポジトリ
* https://github.com/yuezato/xorslp_ec
    * 概要: SC'21の論文（下欄で詳述）用リポジトリ。Erasure codingの高速実装を実現。現時点ではIntelのライブラリ https://github.com/intel/isa-l より高速。
    * 使用言語: Rust
    * やっていること: 有限体の実装, 文法圧縮アルゴリズムの実装, プログラム融合変換, Pebble Gameのヒューリスティック実装, SIMD最適化
* https://github.com/yuezato/minfs
    * 概要: 高級なPersistent KVSをサポートするための、余計なことをしないファイルシステム（VFSではなく実際にディスクに書き込む）
        * 余計なことをしない、というのは例えばLinux Kernelのbioレイヤなどで起こるバッファのフラグメント化を最大限回避し、回避できない場合も巨大なパケット（ATAPIやSATA等のインタフェイスでのmaxとなるように）へ分割し、パケット数を減らす。これはレイテンシを上げるためにも重要。
    * 使用言語: C
    * サブリポジトリ: https://github.com/yuezato/fsprof
        * [eBPF](https://ebpf.io/)を用いてファイルシステムをデバッグするためのスクリプト群
    * モチベーション
        * モチベーション1: [分散システムCephの論文](https://dl.acm.org/doi/10.1145/3341301.3359656)にて、
          分散ファイルシステムの性能は、結局はローカルファイルシステムの性能に左右されるという当たり前のことが指摘されている。
        * モチベーション2: また、[高級な機能を持つファイルシステムに高級なストレージソフトウェアレイヤを被せるのは無駄が多い](https://www.usenix.org/conference/fast14/technical-sessions/presentation/shen)という別の当たり前の結果も指摘されている。
        * よって: 「余計なことは何もしない」ようなplainなファイルシステムを実装し、アプリケーションレイヤ（例えばPersistent KVS等）に書き込みや読み込みの最適化を任せるとどうなるか実験したかった。よって実装した。

## 非個人のContributeしているリポジトリ
* https://github.com/frugalos/frugalos
    * 複数のコンポーネントからなる、分散オブジェクトストレージFrugalos
    * 主な貢献コンポーネント
        * 分散アルゴリズムレイヤ https://github.com/frugalos/raftlog
        * （ローカル）オブジェクトストレージ https://github.com/frugalos/cannyls

## 最近の興味に関する説明 / About my recent interest

プログラムに関する理論を駆使し、様々な分野の未解決問題を解いたり、既存手法を拡張・高速化することに興味があります。

理論的解析を行う道具として、automata theoryやcomputational logic、及びprogramming theoryに精通しています。<br/>
特にautomata theoryに関する博士論文で博士号を取得しています。

大学では上記のようなことをやってきましたが、会社で分散計算を実現するための開発を行い、
新しく色々な領域に関する興味が出てきました（Topicsセクションの最後の部分がそれです）。

例えば、2021年度は、単著論文 https://dl.acm.org/doi/abs/10.1145/3458817.3476204 を書きました。

この論文では、大規模システムで不可欠な問題（Erasure codingの高速化）を、プログラムの理論を用いた理論的解析をもとに大幅に最適化しました。
SCという、HPC分野のトップカンファレンスに採録されています: https://sc21.supercomputing.org/

また本論文に関して、現時点（2022/01)で二件の講演を国内で行っています:
* 千葉工大での講演: https://stair-st.connpass.com/event/232242/
* 情報処理学会プログラミング研究会 PRO での招待講演: https://sigpro.ipsj.or.jp/pro2021-4/program/

# 主な論文 / Publications in chronological order

* Accelerating XOR-based erasure coding using program optimization techniques
    * Yuya Uezato
    * SC'21: Proceedings of the International Conference for High Performance Computing, Networking, Storage and Analysis
    * [ACM](https://dl.acm.org/doi/10.1145/3458817.3476204), [arxiv](https://arxiv.org/abs/2108.02692)
* Configuration Reachability Analysis of Synchronized Recursive Timed Automata
    * Yuya Uezato, [Yasuhiko Minamide](https://sv.c.titech.ac.jp/minamide/index.en.html)
    * 岩波コンピュータソフトウェア 35巻 1号(2018)
    * https://www.jstage.jst.go.jp/article/jssst/35/1/35_1_140/_article/-char/ja
* Monoid-Based Approach to the Inclusion Problem on Superdeterministic Pushdown Automata
    * Yuya Uezato, Yasuhiko Minamide
    * DLT 2016: Developments in Language Theory
    * [Springer](https://link.springer.com/chapter/10.1007%2F978-3-662-53132-7_32)
* Synchronized Recursive Timed Automata
    * Yuya Uezato, Yasuniko Minamide
    * LPAR 2015: Logic for Programming, Artificial Intelligence, and Reasoning
    * [Springer](https://link.springer.com/chapter/10.1007%2F978-3-662-48899-7_18)
* Pushdown Systems with Stack Manipulation
    * Yuya Uezato, Yasuhiko Minamide 
    * ATVA 2013: Automated Technology for Verification and Analysis
    * [Springer](https://link.springer.com/chapter/10.1007%2F978-3-319-02444-8_29)
* Implementing Monadic Total Parser Combinator on Coq
    * Yuya Uezato
    * IPSJ JIP 2012
    * [情報処理学会電子図書館](http://id.nii.ac.jp/1001/00081612/)

# 主な受賞歴 / Awards
* 平成29年度 筑波大学学長表彰
* PPL 2016 発表賞, http://logic.cs.tsukuba.ac.jp/ppl2016/
* 日本ソフトウェア科学会第32回大会学生奨励賞, https://jssst2015.wordpress.com/
* 2014年度コンピュータサイエンス領域奨励賞, https://www.ipsj.or.jp/award/cs-awardee-2014.html
* PPL 2013 論文賞, https://www.pllab.riec.tohoku.ac.jp/ppl2013/PPL2013ronbunshu.html
* 2012年度コンピュータサイエンス領域奨励賞, http://www.ipsj.or.jp/award/cs-awardee-2012.html
