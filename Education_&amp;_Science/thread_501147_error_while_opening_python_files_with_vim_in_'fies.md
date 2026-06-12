---
title: "error while opening python files with vim in 'fiest fawn'"
date: 2007-07-14
forum: Education &amp; Science
---

### Post by asridhar on 2007-07-14
Whenever I try opening any python files with vi after upgrading to 'fiesty fawn' I get the following error:

Error detected while processing /usr/share/vim/vim70/ftplugin/python.vim:
line   24:
E492: Not an editor command: def\)')<cr>
line   25:
E492: Not an editor command: def\)')<cr>
line   26:
E492: Not an editor command: def\)')<cr>
line   27:
E492: Not an editor command: def\)')<cr>
line   45:
E10: \ should be followed by /, ? or &
Press ENTER or type command to continue


After pressing ENTER the files open up correctly but this is an irritating error that I wanted to remove. 

If anybody has faced similar problems and has found a fix would be greatfull for some hints.

Thanks

---

### Post by yabbadabbadont on 2007-07-14
You might try removing vim and then reinstalling it like so ```
sudo apt-get --purge remove vim
sudo apt-get install vim
```

---

### Post by nofrak on 2008-03-17
This is a pretty old problem, but it was still showing up in my system, so here's what I did to stop the messages from coming up: 

First make a backup and then open the file in question with
```

sudo cp /usr/share/vim/vim70/ftplugin/python.vim /usr/share/vim/vim70/ftplugin/python.vim.bak
sudo vim /usr/share/vim/vim70/ftplugin/python.vim

```
(I assume you're using vim, but any other editor will obviously do).

Find the four lines that look like this:
```
nnoremap <silent> <buffer> ]] :call <SID>Python_jump("/^\(class\\|def\)")<cr>
nnoremap <silent> <buffer> [[ :call <SID>Python_jump('?^\(class\\|def\)')<cr>
nnoremap <silent> <buffer> ]m :call <SID>Python_jump('/^\s*\(class\\|def\)')<cr>
nnoremap <silent> <buffer> [m :call <SID>Python_jump('?^\s*\(class\\|def\)')<cr>
```

and comment them out by putting a " at the front of each line, so that they look like this:
```
"nnoremap <silent> <buffer> ]] :call <SID>Python_jump("/^\(class\\|def\)")<cr>
"nnoremap <silent> <buffer> [[ :call <SID>Python_jump('?^\(class\\|def\)')<cr>
"nnoremap <silent> <buffer> ]m :call <SID>Python_jump('/^\s*\(class\\|def\)')<cr>
"nnoremap <silent> <buffer> [m :call <SID>Python_jump('?^\s*\(class\\|def\)')<cr>
```

That doesn't fix the underlying problem (the class and method navigation still won't work), but it stops the error message from showing up.  Better fixes would be welcome

---

### Post by dpollard on 2011-04-12
The expressions using alternation are causing the errors. Separate out 'class' from 'def' :

nnoremap <silent> <buffer> ]] :call <SID>Python_jump('/^class')<cr>
nnoremap <silent> <buffer> ]] :call <SID>Python_jump('/^def')<cr>
nnoremap <silent> <buffer> [[ :call <SID>Python_jump('?^class')<cr>
nnoremap <silent> <buffer> [[ :call <SID>Python_jump('?^def')<cr>
nnoremap <silent> <buffer> ]m :call <SID>Python_jump('/^\s*class')<cr>
nnoremap <silent> <buffer> ]m :call <SID>Python_jump('/^\s*def')<cr>
nnoremap <silent> <buffer> [m :call <SID>Python_jump('?^\s*class')<cr>
nnoremap <silent> <buffer> [m :call <SID>Python_jump('?^\s*def')<cr>

---

