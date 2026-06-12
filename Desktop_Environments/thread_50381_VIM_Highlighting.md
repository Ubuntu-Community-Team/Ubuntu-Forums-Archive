---
title: "VIM Highlighting"
date: 2005-07-20
forum: Desktop Environments
---

### Post by dqsis on 2005-07-20
Hello Ubuntu Friends! 

I have an immergency! I open a FORTRAN file with VIM and I get no syntax highlighting!!!  :???: 

Any ideas why or how I can fix that?

Thank you in advance.

---

### Post by souki on 2005-07-20
do you mean that it does not work only for fortran file?

if syntax highlighting does not work at all, you can activate it this way:
```
:syntax on
```
if syntax highlighting does not work for fortran file, that means vim can not determine the file type. I think vim needs the .f extension in the file name to guess which syntax file to use
If you want to load a syntax file when vim cannot guess it:
```
:so $VIMRUNTIME/syntax/fortran.vim
```
you can use the [tab] completion to expand the $VIMRUNTIME variable

---

### Post by dqsis on 2005-07-20
As you sugested, the solution was:

:syntax on

Quite dumm of me, but never before was it off...

Thanks for the help. Glad we solved it!!!

ps. But how can I always have :syntax on?? I don't want to type it whenever I open my file... I want it always up!!!

---

### Post by rmjokers on 2005-07-20
To make sure it is always on, you can add the line

syntax on

in your ~/.vimrc file.  To find out what other cool things you can put in this configuration file, you can check out:

[http://vim.sourceforge.net/tips/index.php](http://vim.sourceforge.net/tips/index.php)

for lots of vim tips / tricks.

---

