# Pythonの環境構築

## venvを使ったバージョンの切り替え

### Python 3.10系と3.11系を切り替える場合

Python 3.10系(3.10.11)のインストーラー

https://www.python.org/downloads/release/python-31011/

Python 3.11系(3.11.9)のインストーラー

https://www.python.org/downloads/release/python-3119/

### コマンドの説明

コマンドプロンプトを起動する  
(Visual Studo Code内のターミナルでもOK)

インストール済みのPython一覧表示

```bash
py - 0
```

```bash
py - 0
 -V:3.11 *        Python 3.11 (64-bit)
 -V:3.10          Python 3.10 (64-bit)
```

インストール済みのPython一覧表示(インストール先含む)

```bash
py -0p
```

```bash
py -0p
 -V:3.11 *        C:\Users\user\AppData\Local\Programs\Python\Python311\python.exe
 -V:3.10          C:\Users\user\AppData\Local\Programs\Python\Python310\python.exe
```

### 仮想環境構築

バージョンを指定せず仮想環境構築

Version3.11で仮想環境が作られる

```bash
py -m venv 【仮想環境名(ローマ字推奨)】
py -m venv venv
```

バージョンを指定して仮想環境構築

Version3.10で仮想環境が作られる

```bash
py -3.10 -m venv 【仮想環境名(ローマ字推奨)】
py -3.10 -m venv venv310
```

### Python 3.10系で仮想環境構築有効化の流れ

作業フォルダ : `C:\work\python`

作業フォルダに移動

```bash
cd C:\work\python
```

仮想環境構築

```bash
py -3.10 -m venv venv
```

仮想環境有効化

```bash
venv\Scripts\activate
```

仮想環境有効化後の表示

```bash
(venv) C:\work\python
```

仮想環境の無効化

```bash
deactivate
```

仮想環境の削除

venvフォルダを削除するだけ

## Dockerを使った環境構築

```bash
cd docker-python
docker compose up -d
```

compose.yml

```yml
services:
  python:
    build: .
    tty: true
    volumes:
      - ../python:/python
    privileged: true
```

Dockerfile

```Dockerfile
FROM python:3.10
WORKDIR /python
```