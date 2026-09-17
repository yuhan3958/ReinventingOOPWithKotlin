# Reinventing OOP with Kotlin

Kotlin을 통해 객체지향 프로그래밍이 왜 생겨났는지를 처음부터 다시 따라가는 글입니다.

저의 귀여운 코덱스짱이 작성했습니다.

틀리거나 잘못된 내용이 있으면 풀리퀘를 넣어주세요.

문서는 [Typst](https://typst.app/)로 작성되어 있으며 PDF로 빌드할 수 있습니다.

## Requirements

빌드에는 다음이 필요합니다.

* [Typst](https://typst.app/)
* [JetBrainsMonoHangul](https://github.com/Jhyub/JetBrainsMonoHangul)

별도의 Typst 패키지, 이미지, 참고문헌 데이터베이스 등의 외부 리소스는 사용하지 않습니다.

## Project structure

메인 Typst 소스는 다음 위치에 있습니다.

```text
.
├── book/
│   └── first.typ
└── README.md
```

## Build

Typst가 설치되어 있는지 확인합니다.

```sh
typst --version
```

저장소 루트에서 다음 명령을 실행하면 PDF를 빌드할 수 있습니다.

```sh
typst compile book/first.typ
```

빌드가 성공하면 기본적으로 다음 파일이 생성됩니다.

```text
book/first.pdf
```

출력 파일의 위치와 이름을 직접 지정할 수도 있습니다.

```sh
typst compile book/first.typ ReinventingOOPWithKotlin.pdf
```

## Development

문서를 수정하면서 자동으로 다시 빌드하려면 `watch`를 사용할 수 있습니다.

```sh
typst watch book/first.typ
```

파일을 저장할 때마다 PDF가 다시 생성됩니다.

## Font

이 문서는 [JetBrainsMonoHangul](https://github.com/Jhyub/JetBrainsMonoHangul)을 사용합니다.

```typst
#set text(
  font: "JetBrainsMonoHangul",
  size: 12pt,
)
```

먼저 JetBrainsMonoHangul을 설치한 뒤 Typst가 폰트를 정상적으로 인식하는지 확인합니다.

```sh
typst fonts
```

출력 목록에 `JetBrainsMonoHangul`이 있다면 정상적으로 빌드할 수 있습니다.

### 폰트를 시스템에 설치하지 않고 빌드하기

예를 들어 저장소에 다음과 같이 폰트를 둔다면,

```text
.
├── book/
│   └── first.typ
├── fonts/
│   └── ...
└── README.md
```

`--font-path`를 지정해서 빌드할 수 있습니다.

```sh
typst compile book/first.typ --font-path ./fonts
```

자동 빌드에서도 동일하게 사용할 수 있습니다.

```sh
typst watch book/first.typ --font-path ./fonts
```

## Troubleshooting

### `unknown font family: JetBrainsMonoHangul`

Typst가 JetBrainsMonoHangul을 찾지 못한 경우입니다.

먼저 다음 명령으로 인식되는 폰트를 확인하세요.

```sh
typst fonts
```

목록에 `JetBrainsMonoHangul`이 없다면 다음 저장소에서 폰트를 받아 설치하세요.

https://github.com/Jhyub/JetBrainsMonoHangul

또는 폰트 파일을 별도 디렉터리에 두고 `--font-path`를 사용할 수 있습니다.

```sh
typst compile book/first.typ --font-path ./fonts
```

## License

© 2026 Yuhan Kim

이 저작물은 **Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)** 라이선스로 배포됩니다.

저작자를 표시하는 조건으로 복제, 배포 및 수정할 수 있으며, 수정한 저작물 역시 동일한 라이선스로 배포해야 합니다.
