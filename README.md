# SPDX Test Corpus

This repository contains a test corpus for SDPX licenses and exceptions.  Files names have the following [ABNF][rfc5234]:

```abnf
file-name      = percent-encoded-license-expression "/" license-header "/" matches "/" test "." extention
license-header = "license" / "header"
matches        = "match" / "no-match"
test           = 1*(ALPHA / DIGIT / "-")
extention      = "c" / "sh" / "txt"
```

Where `ALPHA` and `DIGIT` are defined in [RFC 5234 appendix B][rfc5234-aB].

`percent-encoded-license-expression` is a `license-expression` defined in the [SPDX 2.1 appendix IV][spdx-2.1-aIV] with [reserved characters][rfc3986-s2.2] [percent encoded][rfc3986-s2.1] as defined in [RFC 3986 section 2][rfc3986-s2].

For example:

* `ISC/header/no-match/trailing-paragraph.c`
* `ISC/header/no-match/trailing-paragraph.sh`
* `ISC/header/match/alternate-copyright.c`
* `ISC/header/match/alternate-copyright.sh`
* `ISC/header/match/and-only.c`
* `ISC/header/match/and-only.sh`
* `ISC/header/match/canonical.c`
* `ISC/header/match/canonical.sh`
* `ISC/license/no-match/trailing-paragraph.txt`
* `ISC/license/match/alternate-copyright.txt`
* `ISC/license/match/and-only.txt`
* `ISC/license/match/canonical.txt`

`GPL-2.0+` would be encoded to `GPL-2.0%2B` and `GPL-3.0 WITH GCC-exception-3.1` would be encoded to `GPL-3.0%20WITH%20GCC-exception-3.1`.

The `canonical` tests represent the wording preferred by the SPDX legal team.
They do not necessarily represent the license author's preferred wording, although in many cases the SPDX legal team and license author will agree on the preferred wording.

The different extentions allow for exercising matching in the presence of different comment markup.

* `c` corresponds to the [C language][C] as defined by [ISO/IEC 9899:2011][C11], and will usually use `/* … */` or `//` for comments.
* `sh` correponds to [POSIX Shell][shell], and will usually use [`#` for comments][shell-comments].
* `txt` corresponds to [text/plain][rfc2046-s4.1], and will usually include no comment markup.

[C]: https://en.wikipedia.org/wiki/C_%28programming_language%29
[C11]: https://www.iso.org/standard/57853.html
[rfc5234]: https://tools.ietf.org/html/rfc5234
[rfc5234-aB]: https://tools.ietf.org/html/rfc5234#appendix-B
[rfc2046-s4.1]: https://tools.ietf.org/html/rfc2046#section-4.1
[rfc3986-s2]: https://tools.ietf.org/html/rfc3986#section-2
[rfc3986-s2.1]: https://tools.ietf.org/html/rfc3986#section-2.1
[rfc3986-s2.2]: https://tools.ietf.org/html/rfc3986#section-2.2
[shell]: http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html
[shell-comments]: http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_03
[spdx-2.1-aIV]: https://spdx.org/spdx-specification-21-web-version#h.jxpfx0ykyb60
