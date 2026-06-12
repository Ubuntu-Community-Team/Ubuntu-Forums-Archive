---
title: "gnome-terminal + transparency + vim"
date: 2012-04-30
forum: Desktop Environments
---

### Post by ishkabob on 2012-04-30
Hi all,

I have a vim color scheme that I use called jellybeans:

[http://www.vim.org/scripts/script.php?script_id=2555]("http://www.vim.org/scripts/script.php?script_id=2555")

and it works as expected except that it kills composite transparency in my gnome-terminal. My $TERM variable is set to xterm-256color and I believe my vimrc settings are correct (shown below):

```
  1 syntax on                                                                                                                                                          
  2 set t_Co=256
  3 set background=dark
  4 colorscheme jellybeans
  5 set cul
  6 hi CursorLine term=none cterm=none ctermbg=236
  7 set number
  8 set ruler
  9 set noerrorbells
 10 set smarttab
 11 "set visualbell
 12 set softtabstop=2
 13 set shiftwidth=2
 14 set tabstop=2
 15 set expandtab
```

I *think* that this is an issue with gnome-terminal as I run this theme with composite transparency in OSX on iterm just fine. Thanks for looking!

---

### Post by ishkabob on 2012-04-30
quick update,

I found that it has to do with the ctermbg settings in my color file. Apparently, under gnome-terminal, when vim sets ctermbg (background) it completely overwrites what gnome-terminal has set. I think there is probably a fundamental difference between how iTerm sets transparency and how gnome-terminal does.

I set most of the ctermbg lines to ctermbg=NONE which has mostly fixed the problem, but the theme itself still looks better and is more functional under iTerm without my edits. Can anyone suggest a terminal whose transparency is set differently? Or perhaps I can set opacity on some higher level within Unity? Thanks

---

