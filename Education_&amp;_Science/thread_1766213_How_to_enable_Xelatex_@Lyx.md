---
title: "How to enable Xelatex @Lyx"
date: 2011-05-24
forum: Education &amp; Science
---

### Post by ALdaperan on 2011-05-24
Hello world..

I am trying to enable Xelatex @Lyx but i have some problems . I am ubuntu 11.04 user and Lyx2.0 . I followed [this tutorial](http://modopemat.info/r/index.php?title=Install_LaTeX/XeTeX_and_xgreek_in_Ubuntu_9.10_(via_TeX_Live_2009)) in order to install Xetex

Then i openned Lyx but i cant enable the option to "use non tex fonts via Xetex/luatex" . I attache a screenshot :
[IMG]http://www.latex-community.org/forum/download/file.php?id=3687[/IMG]
ps1: Lyx's interface is in Greek language
ps2: I have to enable first this option and then use a code in preamble in order to use a font right ? :roll: 

Thanks in advance , waiting for your support  ;)

---

### Post by ALdaperan on 2011-05-24
any help pleaseee

---

### Post by alarichall on 2011-06-19
I also have this problem and would love to have a solution...

---

### Post by alarichall on 2011-06-19
Ah, I found a clearly explained workaround at

[http://askubuntu.com/questions/8302/how-can-the-ubuntu-font-be-used-with-lyx-or-latex](http://askubuntu.com/questions/8302/how-can-the-ubuntu-font-be-used-with-lyx-or-latex)

Just thought I'd post that here. It'd be nice to get Lyx working the way (I assume) it's intended though!

---

### Post by alexyz on 2012-12-12
On Ubuntu 12.04 I enabled in the Lyx UI as follows:

* install packages: texlive-xetex and etoolbox
* in Lyx: Tools > Reconfigure
* close Lyx and restart
* Document > Settings > Fonts > Use non-Tex fonts

---

