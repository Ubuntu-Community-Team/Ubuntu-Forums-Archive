---
title: "Does vim.tiny support colorchemes?"
date: 2015-03-19
forum: Desktop Environments
---

### Post by nibal on 2015-03-19
Strange thing, I had no such problems when i installed 14.04 Ubuntu x64 6 months ago. Using the exact same DVD, I find no vim anymore, only vim.tiny. Furthermore, vim is now provided by vim-gnome, which has many circular dependencies in my system. I need to use colorschemes with vim. Does vim.tiny support them? i get:

```

Error detected while processing /usr/share/vim/vim74/colors/ron.vim:
line   12:
E319: Sorry, the command is not available in this version: let g:colors_name = "ron"

```

ron.vim is provided by vim-runtime. vim.tiny seems to understand .vimrc syntax, but doesn't understand vim colorscheme files. Is there a ron.vim colorscheme file for vim.tiny?
I wouldn't like to install the monster vim has become, since I wouldn't be able to remove it. 
How did the same DVD on the same hardware gives me 2 different vim installations in 6 mos, and could i use vim from a previous distro, when it was still manageable?
Seems that with every distro Linux is becoming more and more complex and difficult to manage :-(

---

### Post by nibal on 2015-03-19
vim.tiny is a barebones version of vim for those that do not use vim often. It doesn't support colorschemes. Fortunately the package vim still exists, and is different than gnome.vim. Glad i could make it work again;-)

---

