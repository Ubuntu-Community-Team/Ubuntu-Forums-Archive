---
title: "Vim syntax coloring"
date: 2005-12-07
forum: Desktop Environments
---

### Post by jordilin on 2005-12-07
I am trying vim and I've noted that vim does not provide syntax coloring by default, is that right? When I open a shell script, or a latex file (even installing support of these languages for vim), it doesn't colorize the code. 
By the way, in emacs, when typing accents and then opening the file again with emacs the character that had an accent appears very small. 
Any suggestions for both questions?
Thanks

---

### Post by arpunk on 2005-12-07
In runtime:
```
:syntax on
```
Or edit */etc/vim/vimrc* and uncomment:
```
" syntax on
```

---

### Post by jrib on 2005-12-07
[QUOTE=jordilin]I am trying vim and I've noted that vim does not provide syntax coloring by default, is that right? When I open a shell script, or a latex file (even installing support of these languages for vim), it doesn't colorize the code. 
By the way, in emacs, when typing accents and then opening the file again with emacs the character that had an accent appears very small. 
Any suggestions for both questions?
Thanks[/QUOTE]

install vim-latexsuite if you are using vim for latex... I use it and it's great.

---

### Post by bryanagee on 2007-05-03
It's a bit strange that the syntax coloring and cursor memory are disabled... does anyone know why that is? Obviously Ubuntu isn't exactly targeted at developers, but it makes extra tweaking work for those of us who want to use it.

---

### Post by HolyJoe on 2007-05-18
I get a error when I set *syntax on* in vimrc and my ubuntu version is 7.04

---

### Post by EndPerform on 2007-05-18
The default Feisty Vim is a slimmed down version.  If you want the full-blown versoin:

```
sudo aptitude install vim-full
```

from a terminal and it will get you everything.  Hope that helps.

---

### Post by HolyJoe on 2007-05-20
Thank you for your help.

But I have a question: Why Ubuntu 7.04 doen't no include vim-full version as default?

---

### Post by binaryspiral on 2007-05-20
Space, plain and simple. 20MB more space for the full install to have features only 10% of users would need. 

Besides most new users gravitate towards Nano or Pico for editing text because they're more ... whats the word... intuitive?

either way, vim full install is good to know. Thanks.

---

### Post by HolyJoe on 2007-05-22
Hi, **binaryspiral** Thank you for your reply.

But the games installed as default is more:D, I think Ubuntu 7.04 begin focus on **entertainment ** than the original use.

---

### Post by engine on 2007-05-28
Good thread! I've now gone for the grown-up install of vim _and_ uninstalled all the games I didn't want <g>

---

### Post by netimen on 2007-10-25
and how to color syntax of files, wich extension is not in lowercase (&#1057;pp, CPP)?

---

### Post by Railsbuntu on 2007-11-06
> **EndPerform said:**
> The default Feisty Vim is a slimmed down version.  If you want the full-blown versoin:

```
sudo aptitude install vim-full
```

from a terminal and it will get you everything.  Hope that helps.

Actually:
```
sudo apt-get isntall vim
```
Is more than enough. vim-full install loads and loads of packages :shock:

---

