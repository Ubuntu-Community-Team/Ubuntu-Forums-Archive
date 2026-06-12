---
title: "Latex font problem"
date: 2010-08-06
forum: Education &amp; Science
---

### Post by larry on 2010-08-06
Dear All,
For reasons it would take long to explain, I need to write a document (well, to be honest I need to generate a figure, but that is changed into a latex document) using Arial. It is the requirement of a journal.
Now after checking out this
[http://www.tug.dk/FontCatalogue/arial/](http://www.tug.dk/FontCatalogue/arial/)
and this

[http://ubuntuforums.org/archive/index.php/t-949293.html](http://ubuntuforums.org/archive/index.php/t-949293.html)

I installed the non-free arial (and many other fonts) via
~$ sudo getnonfreefonts-sys -a (see the end of this post for the long output).

However, if I run pdflatex on this minimal example (saved as new.tex)
 
\documentclass[10pt]{article}
\usepackage[T1]{fontenc}
\usepackage[scaled]{uarial}
\renewcommand*\familydefault{\sfdefault}
\begin{document}
bla bla
\end{document}


I get the following error


$ pdflatex new.tex 
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 restricted \write18 enabled.
entering extended mode
(./new.tex
LaTeX2e <2009/09/24>
Babel <v3.8l> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, loaded.
(/usr/share/texmf-texlive/tex/latex/base/article.cls
Document Class: article 2007/10/19 v1.4h Standard LaTeX document class
(/usr/share/texmf-texlive/tex/latex/base/size10.clo))
(/usr/share/texmf-texlive/tex/latex/base/fontenc.sty
(/usr/share/texmf-texlive/tex/latex/base/t1enc.def))
(/usr/local/share/texmf/tex/latex/ua1/uarial.sty
(/usr/share/texmf-texlive/tex/latex/graphics/keyval.sty)) (./new.aux)
(/usr/local/share/texmf/tex/latex/ua1/t1ua1.fd) [1{/home/lorenzo/.texmf-var/fon
ts/map/pdftex/updmap/pdftex.map}] (./new.aux)
kpathsea: Running mktexpk --mfmode / --bdpi 600 --mag 0+570/600 --dpi 570 ua1r8r
mktexpk: don't know how to create bitmap font for ua1r8r.
kpathsea: Appending font creation commands to missfont.log.
 )
!pdfTeX error: pdflatex (file ua1r8r): Font ua1r8r at 570 not found
 ==> Fatal error occurred, no output PDF file produced!

I really do not know where to bang my head, so any suggestion is really appreciated.
Many thanks

larry


##################################################################
##################################################################
~$ sudo getnonfreefonts-sys -a
--2010-08-06 10:41:12--  [ftp://tug.org/tex/getnonfreefonts/getfont2009](ftp://tug.org/tex/getnonfreefonts/getfont2009)
           => `getfont2009'
Resolving tug.org... 130.225.2.178
Connecting to tug.org|130.225.2.178|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /tex/getnonfreefonts ... done.
==> SIZE getfont2009 ... 20450
==> PASV ... done.    ==> RETR getfont2009 ... done.
Length: 20450 (20K) (unauthoritative)

100%[======================================>] 20,450       113K/s   in 0.2s

2010-08-06 10:41:14 (113 KB/s) - `getfont2009' saved [20450]

----------------------------------------------
Installation directory: /usr/local/share/texmf
----------------------------------------------

Package 'arial-urw':
====================

--2010-08-06 10:41:14--  [http://ctan.org/tex-archive/fonts/urw/arial.zip](http://ctan.org/tex-archive/fonts/urw/arial.zip)
Resolving ctan.org... 192.80.64.33
Connecting to ctan.org|192.80.64.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 252225 (246K) [application/zip]
Saving to: `arial.zip'

100%[======================================>] 252,225      203K/s   in 1.2s

2010-08-06 10:41:16 (203 KB/s) - `arial.zip' saved [252225/252225]

b42b970451bdbd410687bbd5cf78965d  arial.zip                 [MD5sum ok]

Extracting 'ua1.zip' from 'arial.zip'...                    [done]
Extracting 'ua1.zip'...                                     [done]
Extracting 'arial.zip'...                                   [done]
Installing 'ua1.map'...                                     [done]

Package 'classico':
===================

--2010-08-06 10:41:17--  [http://ctan.org/tex-archive/fonts/urw/classico/uop.zip](http://ctan.org/tex-archive/fonts/urw/classico/uop.zip)
Resolving ctan.org... 192.80.64.33
Connecting to ctan.org|192.80.64.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 439462 (429K) [application/zip]
Saving to: `uop.zip'

100%[======================================>] 439,462      316K/s   in 1.4s

2010-08-06 10:41:19 (316 KB/s) - `uop.zip' saved [439462/439462]

815ce3d1c184b9db4f650ab2337239a7  uop.zip                   [MD5sum ok]

Extracting 'uop.zip'...                                     [done]
Installing 'uop.map'...                                     [done]

Package 'dayroman':
===================

--2010-08-06 10:41:20--  [http://ctan.org/tex-archive/fonts/DayRoman/dayroman.zip](http://ctan.org/tex-archive/fonts/DayRoman/dayroman.zip)
Resolving ctan.org... 192.80.64.33
Connecting to ctan.org|192.80.64.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 239544 (234K) [application/zip]
Saving to: `dayroman.zip'

100%[======================================>] 239,544      215K/s   in 1.1s

2010-08-06 10:41:22 (215 KB/s) - `dayroman.zip' saved [239544/239544]

ba37a85d88fba6068c019f628368dd53  dayroman.zip              [MD5sum ok]

--2010-08-06 10:41:22--  [http://ctan.org/tex-archive/fonts/DayRoman/day_t1.zip](http://ctan.org/tex-archive/fonts/DayRoman/day_t1.zip)
Resolving ctan.org... 192.80.64.33
Connecting to ctan.org|192.80.64.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 330396 (323K) [application/zip]
Saving to: `day_t1.zip'

100%[======================================>] 330,396      263K/s   in 1.2s

2010-08-06 10:41:24 (263 KB/s) - `day_t1.zip' saved [330396/330396]

176c1f9699eb3c202f4df634e4f37c2b  day_t1.zip                [MD5sum ok]

Extracting 'dayroman.zip'...                                [done]
Extracting 'day_t1.zip'...                                  [done]
Installing 'dayroman.map'...                                [done]

Package 'eurofont':
===================

--2010-08-06 10:41:25--  [ftp://ftp.adobe.com/pub/adobe/type/win/all/eurofont.exe](ftp://ftp.adobe.com/pub/adobe/type/win/all/eurofont.exe)
           => `eurofont.exe'
Resolving ftp.adobe.com... 192.150.18.26
Connecting to ftp.adobe.com|192.150.18.26|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/adobe/type/win/all ... done.
==> SIZE eurofont.exe ... 172965
==> PASV ... done.    ==> RETR eurofont.exe ... done.
Length: 172965 (169K) (unauthoritative)

100%[======================================>] 172,965      132K/s   in 1.3s

2010-08-06 10:42:16 (132 KB/s) - `eurofont.exe' saved [172965]

93b006d3c2fafb0180d126f04902b733  eurofont.exe              [MD5sum ok]

--2010-08-06 10:42:16--  [http://ctan.org/tex-archive/fonts/euro.zip](http://ctan.org/tex-archive/fonts/euro.zip)
Resolving ctan.org... 192.80.64.33
Connecting to ctan.org|192.80.64.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 116068 (113K) [application/zip]
Saving to: `euro.zip'

100%[======================================>] 116,068      132K/s   in 0.9s

2010-08-06 10:42:18 (132 KB/s) - `euro.zip' saved [116068/116068]

7ff573178eb45f41b8c184b9e0518534  euro.zip                  [MD5sum ok]

Extracting 'eurofont.exe'...                                [done]
Extracting 'euro.zip'...                                    [done]
Processing 'tex europs.ins'...                              [done]
Processing 'pdflatex europs.dtx'...                         [done]
Installing 'zpeu.map'...                                    [done]

Package 'garamond':
===================

--2010-08-06 10:42:20--  [http://ctan.org/tex-archive/fonts/urw/garamond.zip](http://ctan.org/tex-archive/fonts/urw/garamond.zip)
Resolving ctan.org... 192.80.64.33
Connecting to ctan.org|192.80.64.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 393158 (384K) [application/zip]
Saving to: `garamond.zip'

100%[======================================>] 393,158      277K/s   in 1.4s

2010-08-06 10:42:24 (277 KB/s) - `garamond.zip' saved [393158/393158]

a60beaf12c12c69eeb8fdc82bd481949  garamond.zip              [MD5sum ok]

Extracting 'ugm.zip' from 'garamond.zip'...                 [done]
Extracting 'ugm.zip'...                                     [done]
Extracting 'garamond.zip'...                                [done]
Installing 'ugm.map'...                                     [done]

Package 'lettergothic':
=======================

--2010-08-06 10:42:25--  [http://ctan.org/tex-archive/fonts/urw/lettergothic.zip](http://ctan.org/tex-archive/fonts/urw/lettergothic.zip)
Resolving ctan.org... 192.80.64.33
Connecting to ctan.org|192.80.64.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 140528 (137K) [application/zip]
Saving to: `lettergothic.zip'

100%[======================================>] 140,528      154K/s   in 0.9s

2010-08-06 10:42:27 (154 KB/s) - `lettergothic.zip' saved [140528/140528]

1e7a3b31ac405fe90026e950fdd7d93a  lettergothic.zip          [MD5sum ok]

Extracting 'ulg.zip' from 'lettergothic.zip'...             [done]
Extracting 'ulg.zip'...                                     [done]
Extracting 'lettergothic.zip'...                            [done]
Installing 'ulg.map'...                                     [done]

Package 'luximono':
===================

--2010-08-06 10:42:28--  [http://ctan.org/tex-archive/fonts/LuxiMono.zip](http://ctan.org/tex-archive/fonts/LuxiMono.zip)
Resolving ctan.org... 192.80.64.33
Connecting to ctan.org|192.80.64.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 199660 (195K) [application/zip]
Saving to: `LuxiMono.zip'

100%[======================================>] 199,660      188K/s   in 1.0s

2010-08-06 10:42:31 (188 KB/s) - `LuxiMono.zip' saved [199660/199660]

24a5a4ed96993a4018ac99d009446c9e  LuxiMono.zip              [MD5sum ok]

Extracting 'LuxiMono.zip'...                                [done]
Extracting 'ul9.zip' from 'LuxiMono.zip'...                 [done]
Extracting 'ul9.zip'...                                     [done]
Installing 'ul9.map'...                                     [done]

Package 'vntex-nonfree':
========================

--2010-08-06 10:42:32--  [http://vntex.sf.net/fonts/nonfree/vntex-nonfree-3.1.3.zip](http://vntex.sf.net/fonts/nonfree/vntex-nonfree-3.1.3.zip)
Resolving vntex.sf.net... 216.34.181.96
Connecting to vntex.sf.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://vntex.sourceforge.net/fonts/nonfree/vntex-nonfree-3.1.3.zip](http://vntex.sourceforge.net/fonts/nonfree/vntex-nonfree-3.1.3.zip) [following]
--2010-08-06 10:42:34--  [http://vntex.sourceforge.net/fonts/nonfree/vntex-nonfree-3.1.3.zip](http://vntex.sourceforge.net/fonts/nonfree/vntex-nonfree-3.1.3.zip)
Resolving vntex.sourceforge.net... 216.34.181.96
Reusing existing connection to vntex.sf.net:80.
HTTP request sent, awaiting response... 200 OK
Length: 755380 (738K) [application/zip]
Saving to: `vntex-nonfree-3.1.3.zip'

100%[======================================>] 755,380      177K/s   in 4.5s

2010-08-06 10:42:40 (164 KB/s) - `vntex-nonfree-3.1.3.zip' saved [755380/755380]

92c7f48f57fa9c32554e81234da04abf  vntex-nonfree-3.1.3.zip   [MD5sum ok]

Extracting 'vntex-nonfree-3.1.3.zip'...                     [done]
Installing 'garamondvn.map'...                              [done]
Installing 'classicovn.map'...                              [done]

Package 'webomints':
====================

--2010-08-06 10:42:42--  [http://ctan.org/tex-archive/fonts/webomints.zip](http://ctan.org/tex-archive/fonts/webomints.zip)
Resolving ctan.org... 192.80.64.33
Connecting to ctan.org|192.80.64.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 91960 (90K) [application/zip]
Saving to: `webomints.zip'

100%[======================================>] 91,960      99.5K/s   in 0.9s

2010-08-06 10:42:44 (99.5 KB/s) - `webomints.zip' saved [91960/91960]

9eb1d72394e0cf18811072471e8723a4  webomints.zip             [MD5sum ok]

Extracting 'webomints.zip'...                               [done]
Installing 'webo.map'...                                    [done]

texhash: Updating /usr/local/share/texmf/ls-R...
texhash: Done.

Updating map files (updmap-sys)...                          [done]

---

### Post by larry on 2010-08-06
Well, by miracle I found a workaround
[http://bit.ly/afYvWH](http://bit.ly/afYvWH)
Indeed running the command
sudo updmap-sys --enable Map=ua1.map 
sorted out the problem.

larry

---

### Post by FreeTheBee on 2010-08-08
For using non standard fonts it can be handy to use XeTeX instead of pdfLaTeX. It allows you to use many of the regular fonts installed on your system. XeTeX is part of TeXlive.

---

