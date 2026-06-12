---
title: "vim-latexsuite"
date: 2009-06-08
forum: General Help
---

### Post by Shivan on 2009-06-08
Hello everyone, I'm trying to use vim to do some latex, so I installed vim-latexsuite, but I cannot get it to do anything.

I put that in my .vimrc:
filetype plugin on
set grepprg=grep\ -nH\ $*
filetype indent on
set iskeyword+=:
let g:tex_flavor='latex'

but for example:
:nmap \ll bears no mapped command
eqnarray<esc><F5> just complains about F5 not being affected.

anyone enjoyed that sort of pleasures?

---

### Post by Shivan on 2009-06-08
answering to myself:
sudo vim-addons -w install latex-suite

I don't know why, but it was on the system, but not activated.

---

