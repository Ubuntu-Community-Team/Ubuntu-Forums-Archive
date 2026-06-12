---
title: "TeXlive error after upgrading to 10.04"
date: 2010-07-16
forum: Education &amp; Science
---

### Post by riivella on 2010-07-16
Hi, 

after upgrading my server to Ubuntu 10.04 I've got the following error from texlive after an aptitude reinstall tex-common:
> Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following packages will be REINSTALLED:
  tex-common 
The following partially installed packages will be configured:
  context fragmaster latex-cjk-all latex-cjk-chinese latex-cjk-common 
  latex-cjk-japanese latex-cjk-korean latex-cjk-thai latex-cjk-xcjk lmodern 
  musixtex tex-gyre texlive texlive-bibtex-extra texlive-formats-extra 
  texlive-full texlive-games texlive-humanities texlive-lang-cyrillic 
  texlive-lang-czechslovak texlive-lang-polish texlive-latex-extra 
  texlive-latex-recommended texlive-latex3 texlive-math-extra texlive-music 
  texlive-omega texlive-pstricks texlive-publishers texlive-science 
  texlive-xetex thailatex 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information...
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Building format(s) --all.
	This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.J5lfxEfP
Please include this file if you report a bug.

dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lmodern:
 lmodern depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
dpkg: error processing lmodern (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tex-gyre:
 tex-gyre depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing tex-gyre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context:
 context depends on lmodern (>= 1.106); however:
  Package lmodern is not configured yet.
 context depends on tex-gyre; however:
  Package tex-gyre is not configured yet.
 context depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing context (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-common:
 latex-cjk-common depends on tex-common (>= 2.04); however:
  Package tex-common is not configured yet.
dpkg: error processing latex-cjk-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-xetex:
 texlive-xetex depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-xetex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-xcjk:
 latex-cjk-xcjk depends on latex-cjk-common (>= 4.8.2+git20090105-4); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-xcjk depends on texlive-xetex; however:
  Package texlive-xetex is not configured yet.
 latex-cjk-xcjk depends on tex-common (>= 2.04); however:
  Package tex-common is not configured yet.
dpkg: error processing latex-cjk-xcjk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-chinese:
 latex-cjk-chinese depends on latex-cjk-common (= 4.8.2+git20090105-4); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-chinese depends on tex-common (>= 2.04); however:
  Package tex-common is not configured yet.
dpkg: error processing latex-cjk-chinese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-japanese:
 latex-cjk-japanese depends on latex-cjk-common (= 4.8.2+git20090105-4); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-japanese depends on tex-common (>= 2.04); however:
  Package tex-common is not configured yet.
dpkg: error processing latex-cjk-japanese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-korean:
 latex-cjk-korean depends on latex-cjk-common (>= 4.8.2+git20090105-4); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-korean depends on tex-common (>= 2.04); however:
  Package tex-common is not configured yet.
dpkg: error processing latex-cjk-korean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of thailatex:
 thailatex depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
dpkg: error processing thailatex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-thai:
 latex-cjk-thai depends on latex-cjk-common (>= 4.8.2+git20090105-4); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-thai depends on tex-common (>= 2.04); however:
  Package tex-common is not configured yet.
 latex-cjk-thai depends on thailatex (>= 0.4.2); however:
  Package thailatex is not configured yet.
dpkg: error processing latex-cjk-thai (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-all:
 latex-cjk-all depends on latex-cjk-common (>= 4.8.2+git20090105-4); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-all depends on latex-cjk-xcjk (= 4.8.2+git20090105-4); however:
  Package latex-cjk-xcjk is not configured yet.
 latex-cjk-all depends on latex-cjk-chinese (>= 4.8.2+git20090105-4); however:
  Package latex-cjk-chinese is not configured yet.
 latex-cjk-all depends on latex-cjk-japanese (>= 4.8.2+git20090105-4); however:
  Package latex-cjk-japanese is not configured yet.
 latex-cjk-all depends on latex-cjk-korean (= 4.8.2+git20090105-4); however:
  Package latex-cjk-korean is not configured yet.
 latex-cjk-all depends on latex-cjk-thai (= 4.8.2+git20090105-4); however:
  Package latex-cjk-thai is not configured yet.
dpkg: error processing latex-cjk-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of musixtex:
 musixtex depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing musixtex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-latex-recommended (>= 2009-1); however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:
 texlive-bibtex-extra depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-formats-extra:
 texlive-formats-extra depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-formats-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-humanities:
 texlive-humanities depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-humanities (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-czechslovak:
 texlive-lang-czechslovak depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-lang-czechslovak (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-games:
 texlive-games depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-games (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex3:
 texlive-latex3 depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-latex3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-polish:
 texlive-lang-polish depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-lang-polish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-cyrillic:
 texlive-lang-cyrillic depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-lang-cyrillic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fragmaster:
 fragmaster depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing fragmaster (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-music:
 texlive-music depends on musixtex (>= 0.112.2-1); however:
  Package musixtex is not configured yet.
 texlive-music depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-music (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-science:
 texlive-science depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-science (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-publishers:
 texlive-publishers depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-publishers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-omega:
 texlive-omega depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-omega (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-full:
 texlive-full depends on texlive-humanities (>= 2009-1); however:
  Package texlive-humanities is not configured yet.
 texlive-full depends on texlive-lang-czechslovak (>= 2009-1); however:
  Package texlive-lang-czechslovak is not configured yet.
 texlive-full depends on texlive-games (>= 2009-1); however:
  Package texlive-games is not configured yet.
 texlive-full depends on texlive-math-extra (>= 2009-1); however:
  Package texlive-math-extra is not configured yet.
 texlive-full depends on texlive-latex3 (>= 2009-1); however:
  Package texlive-latex3 is not configured yet.
 texlive-full depends on texlive-formats-extra (>= 2009-1); however:
  Package texlive-formats-extra is not configured yet.
 texlive-full depends on texlive-lang-polish (>= 2009-1); however:
  Package texlive-lang-polish is not configured yet.
 texlive-full depends on texlive-pstricks (>= 2009-1); however:
  Package texlive-pstricks is not configured yet.
 texlive-full depends on texlive-lang-cyrillic (>= 2009-1); however:
  Package texlive-lang-cyrillic is not configured yet.
 texlive-full depends on texlive-latex-extra (>= 2009-1); however:
  Package texlive-latex-extra is not configured yet.
 texlive-full depends on fragmaster; however:
  Package fragmaster is not configured yet.
 texlive-full depends on texlive-music (>= 2009-1); however:
  Package texlive-music is not configured yet.
 texlive-full depends on texlive-science (>= 2009-1); however:
  Package texlive-science is not configured yet.
 texlive-full depends on texlive-xetex (>= 2009-1); however:
  Package texlive-xetex is not configured yet.
 texlive-full depends on texlive-publishers (>= 2009-1); however:
  Package texlive-publishers is not configured yet.
 texlive-full depends on texlive-bibtex-extra (>= 2009-1); however:
  Package texlive-bibtex-extra is not configured yet.
 texlive-full depends on context; however:
  Package context is not configured yet.
 texlive-full depends on texlive-latex-recommended (>= 2009-1); however:
  Package texlive-latex-recommended is not configured yet.
 texlive-full depends on texlive-omega (>= 2009-1); however:
  Package texlive-omega is not configured yet.
dpkg: error processing texlive-full (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 lmodern
 tex-gyre
 context
 latex-cjk-common
 texlive-xetex
 latex-cjk-xcjk
 latex-cjk-chinese
 latex-cjk-japanese
 latex-cjk-korean
 thailatex
 latex-cjk-thai
 latex-cjk-all
 musixtex
 texlive-latex-recommended
 texlive
 texlive-bibtex-extra
 texlive-formats-extra
 texlive-humanities
 texlive-lang-czechslovak
 texlive-games
 texlive-math-extra
 texlive-latex3
 texlive-lang-polish
 texlive-pstricks
 texlive-lang-cyrillic
 texlive-latex-extra
 fragmaster
 texlive-music
 texlive-science
 texlive-publishers
 texlive-omega
 texlive-full
Setting up tex-common (2.06) ...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...

Does anyone got an idea how to solve this?

---

### Post by gunksta on 2010-07-16
The error message you received says:

```
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.J5lfxEfP
```

I would start by looking in this file to see what the error was when running fmtutil-sys

What PPAs / alternative repos did you have installed before upgrading?

---

### Post by riivella on 2010-07-17
Thank you for the hint. I found the problem.

In the file /tmp/fmtutil.J5lfxEfP there were some messages like
> ! TeX capacity exceeded, sorry [pattern memory=400000].
l.5614 2oni4c
             
!  ==> Fatal error occurred, no output PDF file produced!
So I changed the parameter trie_size in /etc/texmf/texmf.cnf and it works fine now.

---

