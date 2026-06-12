---
title: "Higlighting key words on terminal"
date: 2006-01-13
forum: General Help
---

### Post by jsmidt on 2006-01-13
I am trying to write a program in C.  The key words like "for" and "if" are not highlighting.  I am naming my files .c.  How do I turn on highlighting key words like "for" and "if".  It also isn't highlighting key words in my .tex files. Thanks. :)

---

### Post by oakz on 2006-01-13
the answer will depend on the text editor you are using and if it supports syntax highlighting....what editor are you using?

---

### Post by jsmidt on 2006-01-13
I am using vim.

---

### Post by oakz on 2006-01-13
while in vim enter ":syn on"

you can have vim automatically turn on syntax highlighting by adding "syntax on" to your ~/.vimrc file.

---

### Post by jsmidt on 2006-01-14
I don't see a ~/.vimrc file.  I did 
```

ls -a

``` 

How do I get one?  Do I have to configure vim?

---

### Post by healychan on 2006-01-14
[QUOTE=jsmidt]I don't see a ~/.vimrc file.  I did 
```

ls -a

``` 

How do I get one?  Do I have to configure vim?[/QUOTE]
When you do "ls -a", what directory was you in??

---

### Post by jsmidt on 2006-01-14
I was in my home directory.

---

### Post by oakz on 2006-01-14
Do the following in a terminal:

$ cp /usr/share/vim/vimrc ~/.vimrc

Then edit ~/.vimrc and uncomment the following line by removing the " at the beginning of the line:
" syntax on

---

### Post by jsmidt on 2006-01-14
Thanks a lot! :smile:

---

