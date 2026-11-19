# kanmon-data

[kanmon](https://github.com/zephel01/kanmon) が使うデータを配るリポジトリです。コードは置きません。

## AS のデータ（Release「asn-data」）

kanmon（v0.5.1〜）が、宛先の AS・回線の種類（クラウド / CDN / 住宅用）・登録国を手元で引くためのデータです。

| ファイル | 中身 |
|---|---|
| `asn.kasn.gz` | KASN1 形式（gzip、約 3MB）。範囲・AS 番号・国は全部、AS の名前は kanmon の一覧にある AS だけ |
| `asn.kasn.gz.sha256` | 上の SHA-256。kanmond はこれを照合する |

- 更新：`.github/workflows/asn-data.yml` が週 1 回（月曜 3:17、日本時間）、iptoasn.com から取り、kanmon の `tools/asn-data/build_asn.py` で縮める。中身が変わったときだけ差し替える
- 利用者の kanmond は iptoasn.com には行かず、ここから 7 日ごとに `.sha256` を見て、変わっていれば取る
- 形式と作り方は kanmon の [tools/asn-data/README.md](https://github.com/zephel01/kanmon/blob/main/tools/asn-data/README.md) を見てください

## ライセンス

元データは [iptoasn.com](https://iptoasn.com/) のもので、Public Domain（PDDL v1.0）です。
