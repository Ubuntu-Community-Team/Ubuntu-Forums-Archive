---
title: "Latexsuite error: unknown function IMAP"
date: 2007-04-25
forum: Desktop Environments
---

### Post by beijon on 2007-04-25
Hi,

I just installed Xubuntu, and to my great horror, my beloved latexsuite (in vim) doesn't work properly! It gives these errors when opening any .tex file:

error detected while processing /usr/share/vim/vim70/ftplugin/latex-suite/main.vim:
E117: unknown function: IMAP
Error detected while processing function <SNR>30_Tex_SpecialMacros

and so on. Then none of the neat features in latexsuite work, like key bindings or folding.

I would be most grateful for any ideas about how to solve this....

---

### Post by thisllub on 2007-12-19
This one has been around for a while but here is a solution.

The Ubuntu VIM Latex install just doesn't work.

Go to this page, download and install as per the instructions. 

[http://vim-latex.sourceforge.net/index.php?subject=download](http://vim-latex.sourceforge.net/index.php?subject=download)


Ubuntu puts the files in usr/share/vim
instead of ~/.vim

---

