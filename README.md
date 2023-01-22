# コンパイラ別のバイナリ比較

## 検証用コード

```csharp
using System;

namespace ConsoleApp1
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("test");
            Console.ReadLine();
        }
    }
}
```

## 参考

- [OSに標準付属のMSBuildツールでプロジェクトをビルドするには？](https://atmarkit.itmedia.co.jp/ait/articles/1505/13/news016.html)
- [MSBuild の予約済みおよび既知のプロパティ](https://learn.microsoft.com/ja-jp/visualstudio/msbuild/msbuild-reserved-and-well-known-properties)

## おまけ

`csc.exe /help

```txt
Microsoft (R) Visual C# 2008 Compiler version 3.5.30729.9151
for Microsoft (R) .NET Framework version 3.5
Copyright (C) Microsoft Corporation. All rights reserved.

                        Visual C# 2008 コンパイラのオプション

                        - 出力ファイル -
/out:<ファイル>                出力ファイル名を指定します (既定: メイン クラスかファースト
                               ファイルを伴うファイルのベース名)。
/target:exe                    コンソール アプリケーションをビルドします (既定)。 (短い形式: /t:exe)
/target:winexe                 Windows 実行可能ファイルをビルドします。 (短い形式: /t:winexe)
/target:library                ライブラリをビルドします。 (短い形式: /t:library)
/target:module                 別のアセンブリに追加できるモジュールをビルドします。 (短い形式: /t:module)
/delaysign[+|-]                厳密な名前のキーのパブリックな部分のみを使ってアセンブリを遅延署名します。
/doc:<ファイル>                生成する XML ドキュメント ファイル
/keyfile:<ファイル>            厳密な名前のキー ファイルを指定します。
/keycontainer:<文字列>         厳密な名前のキー コンテナを指定します。
/platform:<文字列>             このコードが実行されるプラットフォームの制限: x86、Itanium、x64、または anycpu。既定は
                               anycpu です。

                        - 入力ファイル -
/recurse:<ワイルドカード>      ワイルドカードの指定に従い、現在のディレクトリとサブディレクトリ内のすべてのファイルをイ
                               ンクルードします。
/reference:<エイリアス>=<ファイル>
                               指定されたエイリアスを使用して、指定されたアセンブリ ファイルからメタベースを参照する
                               (短い形式: /r)
/reference:<ファイル リスト>   指定されたアセンブリ ファイルからメタベースを参照する (短い形式: /r)
/addmodule:<ファイル リスト>   指定されたモジュールをこのアセンブリにリンクする

                        - リソース -
/win32res:<ファイル>           Win32 リソース ファイルを指定します (.res)。
/win32icon:<ファイル>          出力にこのアイコンを使用します。
/win32manifest:<ファイル>      Win32 マニフェスト ファイル (.xml) を指定してください。
/nowin32manifest               既定の Win32 マニフェストを含めません。
/resource:<リソース情報>       指定したリソースを埋め込みます。 (短い形式: /res)
/linkresource:<リソース情報>   このアセンブリに指定されたリソースをリンクします。 (短い形式: /linkres)
                               リソース情報の形式は <ファイル>[,<文字列名>
                               [,public|private]] です。

                        - コード生成 -
/debug[+|-]                    デバッグ情報を生成する
/debug:{full|pdbonly}          デバッグの種類を指定します (既定値は full
                               で、実行中のプログラムにデバッガを付加することができます)。
/optimize[+|-]                 最適化を有効にする (短い形式: /o)

                        - エラーと警告 -
/warnaserror[+|-]              すべての警告をエラーとして報告する
/warnaserror[+|-]:<警告リスト> 指定した警告をエラーとして報告する
/warn:<n>                      警告レベル (0-4) を設定する (短い形式: /w)
/nowarn:<警告リスト>           指定の警告メッセージを無効にする

                        - 言語 -
/checked[+|-]                  オーバーフロー チェックの生成
/unsafe[+|-]                   アンセーフ コードの許可
/define:<シンボル リスト>      条件付きコンパイル シンボルを定義する (短い形式: /d)
/langversion:<文字列>          言語バージョン モードの指定: ISO-1、ISO-2、または Default

                        - その他 -
@<ファイル>                    応答ファイルを読み取り、オプションを追加します。
/help                          この使用法のメッセージを表示します。 (短い形式: /?)
/nologo                        コンパイル時の著作権メッセージを表示しません。
/noconfig                      CSC.RSP ファイルを自動的に含めません。

                        - 詳細 -
/baseaddress:<アドレス>        ビルドするライブラリのベース アドレスです。
/bugreport:<ファイル>          'バグ報告' ファイルを作成します
/codepage:<n>                  ソース ファイルを開くときに使用するコードページを指定します。
/utf8output                    UTF-8 エンコードでコンパイラのメッセージを出力する
/main:<型>                     エントリ ポイントを含む型を指定します (他のエントリ ポイントはすべて無視します)。
                               (短い形式: /m)
/fullpaths                     コンパイラは絶対パスを生成します。
/filealign:<n>                 出力ファイル セクションで使用する配置を指定します。
/pdb:<ファイル>                デバッグ情報ファイル名を指定します (既定: .pdb 拡張子の付いた出力ファイル名)
/nostdlib[+|-]                 標準ライブラリ (mscorlib.dll) を参照しない
/lib:<ファイル リスト>         参照を検索する追加のディレクトリを指定します。
/errorreport:<文字列>          内部コンパイラ エラーの処理方法を指定します: prompt、send、queue、または none
                               です。既定値は queue です。
/moduleassemblyname:<文字列>   このモジュールが一部となるアセンブリ名です
```