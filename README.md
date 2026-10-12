# LaTeX Project Template

## 概要

LaTeXを使ったレポート、論文、卒業論文などの作成を始めるためのテンプレートです。Visual Studio CodeのDev Containerを使って、開発環境をコンテナ内にそろえられます。

## 主な機能

- **Dev Container**: Ubuntuベースの開発コンテナを構築します。
- **LaTeX Workshop**: LaTeXの編集、保存時のビルド、ChkTeXによるLintなどをVS Codeに設定します。
- **LaTeX関連ツール**: コンテナに`chktex`と`texlive-extra-utils`をインストールします。
- **latexmk設定**: `.latexmkrc`でpLaTeX、pBibTeX、dvipdfmxを使うビルド設定を用意しています。

`uv`、`pytest`、`Ruff`はこのテンプレートには設定・インストールされていません。Pythonを使う場合は、必要に応じて`pyproject.toml`やDev Containerの設定に追加してください。

## 前提条件

- Git
- Visual Studio Code
- VS Code拡張機能「Dev Containers」

## 使用方法

1. GitHubで「Use this template」を選び、新しいリポジトリを作成します。利用できない場合は、このリポジトリを複製して新しいリポジトリをremoteに設定し、pushしてください。

   ```sh
   git clone https://github.com/<your-account>/<your-repository>.git
   cd <your-repository>
   ```

2. リポジトリをVS Codeで開きます。
3. VS Codeのコマンドパレットから「Dev Containers: Reopen in Container」を実行します。
4. プロジェクトのLaTeXファイル（例: `main.tex`）を作成し、文書の作成を始めます。

## ディレクトリ構成

```text
.
├── .devcontainer/
│   ├── devcontainer.json    # コンテナとVS Code拡張機能・設定
│   └── Dockerfile           # 開発コンテナのイメージ定義
├── .github/
│   ├── copilot-instructions.md  # Copilot向けのリポジトリ指示
│   └── skills/                  # Copilotスキル
│       ├── acquire-codebase-knowledge/
│       └── conventional-commit/
├── .gitignore               # Gitの追跡対象から除外するファイル
├── .latexmkrc               # latexmkのLaTeX・BibTeXビルド設定
└── README.md                # このファイル
```

## 開発手順

### コンテナを起動する

VS Codeで「Dev Containers: Reopen in Container」を実行します。Dockerfileや`devcontainer.json`を変更した場合は、「Dev Containers: Rebuild Container」でコンテナを再構築してください。

### 依存関係を用意する

Dockerfileでは`chktex`と`texlive-extra-utils`をインストールします。`.latexmkrc`で指定しているpLaTeXなどのエンジンを使うには、利用する文書に応じたTeX Liveのパッケージが別途必要になる場合があります。必要なツールはDockerfileに追加してください。


### ビルド・テストを実行する

LaTeX文書を作成したら、`latexmk`でビルドできます。

```sh
latexmk main.tex
```


## カスタマイズ方法

- **プロジェクト名**: VS Codeで表示されるコンテナ名は`.devcontainer/devcontainer.json`の`name`で変更できます。GitHubで作成したリポジトリ名や文書のタイトルも、必要に応じて更新してください。
- **LaTeXの設定**: エンジン、文献処理、PDF生成方法は`.latexmkrc`で変更します。使うTeX Liveパッケージやシステムツールは`.devcontainer/Dockerfile`に追加してください。
- **Pythonの依存関係・品質チェック**: Pythonプロジェクトとして使う場合は`pyproject.toml`に依存関係とRuffの設定を追加し、テストコードを作成してください。Dev Container内で`uv`を利用するには、そのインストール手順もDockerfileなどに追加します。
- **VS Codeの設定**: 利用する拡張機能や保存時の動作は`.devcontainer/devcontainer.json`で変更できます。