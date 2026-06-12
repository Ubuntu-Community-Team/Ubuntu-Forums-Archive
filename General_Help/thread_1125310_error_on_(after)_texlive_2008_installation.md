---
title: "error on (after) texlive 2008 installation"
date: 2009-04-14
forum: General Help
---

### Post by newway on 2009-04-14
I am trying to install texlive 2008 on my Ubuntu 8.10 (32bit) laptop with the downloaded iso image mounted.

everything seems fine but the install-tl.log showed the following error:

running mktexlsr /usr/local/texlive/2008/texmf-var
running updmap-sys... /usr/local/texlive/2008/bin/i386-linux/updmap-sys: 1: Syntax error: word unexpected (expecting ")")
done
re-running mktexlsr /usr/local/texlive/2008/texmf-var
pre-generating all format files (fmtutil-sys --all), be patient.../usr/local/texlive/2008/bin/i386-linux/fmtutil-sys: 1: Syntax error: Unterminated quoted string
done
./install-tl: done.

and if I dare to run, e.g. pdflatex
it will give a bunch of gibberish errors such as:
/usr/local/texlive/2008/bin/i386-linux/pdflatex: line 9: l&#65533;&#65533;f&#65533;2F/z&#65533;&#65533;5&#65533;L: No such file or directory
/usr/local/texlive/2008/bin/i386-linux/pdflatex: line 9: &#65533;oo&#1385;*1&#65533;j&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;@&#65533;&#65533;&#65533;Vfm&#65533;&#65533;r&#65533;&#65533;&#65533;s&#65533;&#65533;u&#65533;&#65533;&#65533;&#65533;&#65533;j&#65533;9&#65533;W&#1638;&#65533;&#65533;=&#65533;&#65533;&#65533;&#65533;8n&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;b&#65533;&#65533;x&#65533;: command not found

strange enough that I have successfully installed texlive 2008 (same image file) on another desktop running ubuntu 8.04

---

