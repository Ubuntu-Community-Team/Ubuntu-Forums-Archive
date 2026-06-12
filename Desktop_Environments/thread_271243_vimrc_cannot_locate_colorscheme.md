---
title: "vimrc cannot locate colorscheme"
date: 2006-10-04
forum: Desktop Environments
---

### Post by adamthetownkrier on 2006-10-04
I have a clean install of ubuntu server 6.06 and an existing install of 6.06 desktop, both of which have a vimrc file (one in ~/.vimrc and the other in /etc/vim/vimrc)... they both have an identical line that says

colorscheme elflord

Whenever i try to edit a file with vim, i get the following output:
Error detected while processing /home/asmieszny/.vimrc:
line   86:
E185: Cannot find color scheme elflord
Hit ENTER or type command to continue

I have tried modifying the line to read:
colorscheme elflord.vim
and
colorscheme /usr/share/vim/vim64/colors/elflord.vim

and i have added /usr/share/vim/vim64/ to my PATH, none of which have helped.

For some reason vim can not locate my colorscheme. Can anyone please advise?

Thanks,
Adam

---

### Post by mitch.c on 2006-10-04
> **adamthetownkrier said:**
> 
Whenever i try to edit a file with vim, i get the following output:
Error detected while processing /home/asmieszny/.vimrc:
line   86:
E185: Cannot find color scheme elflord
Hit ENTER or type command to continue

I have tried modifying the line to read:
colorscheme elflord.vim
and
colorscheme /usr/share/vim/vim64/colors/elflord.vim

and i have added /usr/share/vim/vim64/ to my PATH, none of which have helped.

For some reason vim can not locate my colorscheme. Can anyone please advise?

Thanks,
Adam

Your problem is most likely:
```
colorscheme elflord.vim
```

This should be:
```
colorscheme elflord
```

If not...

Does /usr/share/vim/vim64/colors/elflord.vim exist? What hapens if vim if you do:
```
:colorscheme elflord
```

What is the output (from within vim) from the following three commands:
```
:!echo $VIMRUNTIME
:!echo $VIM
:set runtimepath?
```

---

### Post by adamthetownkrier on 2006-10-04
Mitch:

Thank you for your reply. I originally had (and currently have)
colorscheme elflord

I tried colorscheme elflord.vim and (as you said) that definitely did not work...

The command :colorscheme elflord within vim returned the same message.... could not find colorscheme

The colors directory definitely has the scheme

$ ls /usr/share/vim/vim64/colors/
blue.vim      delek.vim    evening.vim  murphy.vim     README.txt  torte.vim
darkblue.vim  desert.vim   koehler.vim  pablo.vim      ron.vim     zellner.vim
default.vim   elflord.vim  morning.vim  peachpuff.vim  shine.vim


------
BUT
------

your last recommendation about those environment variables was spot on.
I had the $VIMRUNTIME set to /usr/share/vim/vim64
and $VIM set to /user/share/vim

but the runtimepath that i had set referenced /usr/share/vim/vim63...
So i modified that file and now it can find the colorscheme.

Thanks Mitch!

---

