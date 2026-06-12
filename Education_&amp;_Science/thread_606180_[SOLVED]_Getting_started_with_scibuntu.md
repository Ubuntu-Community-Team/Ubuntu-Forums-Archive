---
title: "[SOLVED] Getting started with scibuntu"
date: 2007-11-07
forum: Education &amp; Science
---

### Post by PacoCrespo on 2007-11-07
Hello, I've just arrived to Ubuntu and I have installed Scibuntu version 021-alfa, I'm used to use the WinEdit (from my past with windows) and now I need a help to compile files .tex and get .dvi or oder formats like .pdf.

I guest there is any document somewhere to get started with it

Thank you in advance

:popcorn:

---

### Post by dandyx on 2007-11-08
Hej!
You could try

[https://help.ubuntu.com/community/LaTeX](https://help.ubuntu.com/community/LaTeX)

I am fine with TeXlive. If you want a editor that supports LaTeX you seem to have to choose between Emacs and Vim. I use Vim with a graphical interface (System > Synaptic Package Manager : vim-gtk). You should also install vim-addon-manager. 
After the install write in a console: 
sudo vim-addons -w install latex-suite
([https://bugs.launchpad.net/ubuntu/+source/vim-latexsuite/+bug/137205](https://bugs.launchpad.net/ubuntu/+source/vim-latexsuite/+bug/137205))
'cd' into the directory where your tex-file lives and type
gvim filename.tex
After editing and saving a tex-file in Vim type
'Esc' :!latex filename.tex
and the file is compiled and you get a dvi-file. In order to get a pdf-file write
'Esc' :!dvipdf filename.dvi


Vim is way more complicated than 'normal' editors but it's worth the trouble if you are writing a lot of scientific text.
Hope this helps!

---

### Post by xadder on 2007-11-08
I also use good-old vi most of the time, but I did like gedit+ the latex plugin when I tried it..... very user friendly.

Many use kile, and that also seems very good. 

I tried vim-latex, but that seems to be a dead project, and caused me all kinds of problems (seemed fantastic at first, but then the wrong key-combination adds stuff that often isn't wanted).

---

### Post by LaserJock on 2007-11-08
> **dandyx said:**
> I am fine with TeXlive. If you want a editor that supports LaTeX you seem to have to choose between Emacs and Vim.  

Yikes, talk about dumping somebody in the deep end :-)

Besides emacs/vim (very powerful editors with steep learning curves) there is also gedit (gnome editor), kile (KDE TeX editor), LyX, and TexMaker off the top of my head.

> **dandyx said:**
> 
You should also install vim-addon-manager.
After the install write in a console:
sudo vim-addons -w install latex-suite
([https://bugs.launchpad.net/ubuntu/+source/vim-latexsuite/+bug/137205](https://bugs.launchpad.net/ubuntu/+source/vim-latexsuite/+bug/137205))
'cd' into the directory where your tex-file lives and type
gvim filename.tex
After editing and saving a tex-file in Vim type
'Esc' :!latex filename.tex
and the file is compiled and you get a dvi-file. In order to get a pdf-file write
'Esc' :!dvipdf filename.dvi


Another yikes! You shouldn't need to do a vim-addon-manager workaround for latex-suite. Thanks for bringing up that bug report, it looks like a trivial fix and I'll see if I can get that done for Hardy.

-LaserJock

---

### Post by PacoCrespo on 2007-11-13
Thank you it was very helpfull

---

