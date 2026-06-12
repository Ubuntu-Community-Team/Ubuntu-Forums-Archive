---
title: "How to associate file with a program"
date: 2006-02-15
forum: Desktop Environments
---

### Post by peyu on 2006-02-15
Hi all,

I'm trying to associate a file with an application, but it doesn't work. :-k 
I'm using Ubuntu 5.10.

I do right click on the file > properties > open with, and I select the application.

But when I validate, I've got an error message : "cannot add the application to the base"

Did I make something wrong ?

Thks.

---

### Post by dcstar on 2006-02-16
[QUOTE=peyu]Hi all,

I'm trying to associate a file with an application, but it doesn't work. :-k 
I'm using Ubuntu 5.10.

I do right click on the file > properties > open with, and I select the application.

But when I validate, I've got an error message : "cannot add the application to the base"

Did I make something wrong ?

Thks.[/QUOTE]
Exactly what sort of file?

---

### Post by peyu on 2006-02-16
Well, basically I tried to associate php files with gPHPEdit, but it doesn't work either with others extensions (I tried ini, png...)

It always display the error "can not add the application to the base" :???:

---

### Post by mcduck on 2006-02-16
check that you own ~/.local and everything inside it, and that you have read/write access there.

I had the same problem once with Hoary, and the problem was that this directory had someway become owned by root..

---

### Post by peyu on 2006-02-16
Thanks you, it works. My own /.local was owned by root.

---

