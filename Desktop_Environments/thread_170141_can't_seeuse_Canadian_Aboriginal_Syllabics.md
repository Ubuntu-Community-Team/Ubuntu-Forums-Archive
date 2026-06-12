---
title: "can't see/use Canadian Aboriginal Syllabics"
date: 2006-05-04
forum: Desktop Environments
---

### Post by civetta on 2006-05-04
I can't seem to see Aboriginal Syllabics. All I get is the Hex when I use the character map, or view pages with syllabics on firefox 1.5.

I'm using Dapper beta, but I had the same problem with Breezy. Following advice from another forum, here's what I got from dpkg-query -l | grep font if it helps:

ii  console-data                           2002.12.04dbs-52.1ubuntu9  Keymaps, fonts, charset maps, fallback table
ii  console-tools                          0.2.3dbs-60ubuntu3  Linux console and font utilities
ii  defoma                                 0.11.8ubuntu2  Debian Font Manager -- automatic font config
ii  fnlib-data                             0.5-13  font files needed by Fnlib
ii  fontconfig                             2.3.2-1.1ubuntu11  generic font configuration library
ii  gsfonts                                8.14+v8.11+urw-0.2  Fonts for the Ghostscript interpreter(s)
ii  gucharmap                              1.6.0-0ubuntu1  Unicode character picker and font browser
ii  latex-xft-fonts                        0.1-5  Xft-compatible versions of some LaTeX fonts
ii  libconsole                             0.2.3dbs-60ubuntu3  Shared libraries for Linux console and font
ii  libfnlib0                              0.5-13  a special font rendering library used by Enl
ii  libfontconfig1                         2.3.2-1.1ubuntu11  generic font configuration library (shared l
ii  libfontenc1                            1.0.1-0ubuntu2  X11 font encoding library
ii  libfreetype6                           2.1.10-1ubuntu2  FreeType 2 font engine, shared library files
ii  libt1-5                                5.1.0-2  Type 1 font rasterizer library - runtime
ii  libxfont1                              1.0.0-0ubuntu3  X11 font rasterisation library
ii  libxft2                                2.1.8.2-0ubuntu2  FreeType-based font drawing library for X
ii  mplayer-fonts                          3.5-2  Fonts for mplayer
ii  msttcorefonts                          1.2ubuntu2  Installer for Microsoft TrueType core fonts
ii  ttf-arabeyes                           1.1-4  Arabeyes GPL TrueType Arabic fonts
ii  ttf-arphic-bkai00mp                    2.10-6.1  "AR PL KaitiM Big5" Chinese TrueType font by
ii  ttf-arphic-bsmi00lp                    2.10-6  "AR PL Mingti2L Big5" Chinese TrueType font
ii  ttf-arphic-gbsn00lp                    2.11-6  "AR PL SungtiL GB" Chinese TrueType font by
ii  ttf-arphic-gkai00mp                    2.11-6  "AR PL KaitiM GB" Chinese TrueType font by A
ii  ttf-baekmuk                            2.2-1ubuntu1  Baekmuk series TrueType fonts
ii  ttf-bengali-fonts                      0.4.7  Free TrueType fonts for the Bengali language
ii  ttf-dejavu                             2.5-0ubuntu2  Bitstream Vera fonts with additional charact
ii  ttf-devanagari-fonts                   0.4.7  Free TrueType fonts for languages using the
ii  ttf-freefont                           20060126b-2ubuntu1  Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-gujarati-fonts                     0.4.7  Free TrueType fonts for the Gujarati languag
ii  ttf-indic-fonts                        0.4.7  Metapackage for free Indian language fonts
ii  ttf-kannada-fonts                      0.4.7  Free TrueType fonts for the Kannada language
ii  ttf-kochi-gothic                       1.0.20030809-3  Kochi Subst Gothic Japanese TrueType font wi
ii  ttf-kochi-mincho                       1.0.20030809-3  Kochi Subst Mincho Japanese TrueType font wi
ii  ttf-lao                                0.0.20060226-1build1  TrueType font for Lao language
ii  ttf-malayalam-fonts                    0.4.7  Free TrueType fonts for the Malayalam langua
ii  ttf-mgopen                             1.1-2  Magenta Open Truetype fonts
ii  ttf-opensymbol                         2.0.2-2ubuntu5  The OpenSymbol TrueType font
ii  ttf-oriya-fonts                        0.4.7  Free TrueType fonts for the Oriya language
ii  ttf-punjabi-fonts                      0.4.7  Free TrueType fonts for the Punjabi language
ii  ttf-tamil-fonts                        0.4.7  Free TrueType fonts for the Tamil language
ii  ttf-telugu-fonts                       0.4.7  Free TrueType fonts for the Telugu language
ii  ttf-thai-tlwg                          0.4.4-0ubuntu1  Thai fonts in TrueType format
ii  x-ttcidfont-conf                       20ubuntu1  Configure TrueType and CID fonts for X
ii  xfonts-100dpi                          6.8.2.1-5  100 dpi fonts for X
ii  xfonts-75dpi                           6.8.2.1-5  75 dpi fonts for X
ii  xfonts-base                            6.8.2.1-5  standard fonts for X
ii  xfonts-scalable                        6.8.2.1-5  scalable fonts for X
ii  xfonts-utils                           6.8.2.1-5  utilities for X font packages
ii  xfontsel                               1.0.1-0ubuntu1  X client - xfontsel
ii  xlsfonts                               1.0.1-0ubuntu1  X client - xlsfonts

Any suggestions?

---

### Post by elamericano on 2006-05-04
All I did was enable bitmap fonts:

sudo dpkg-reconfigure fontconfig

I selected Native, Automatic, Yes (for bitmaps by default)

After that I could see the Canadian Aboriginal Fonts in the character map. Close and reopen Firefox and this may show you something. I don't know any html pages with the font, so I couldn't check.

---

### Post by civetta on 2006-05-04
Thanks!

That did it.

---

