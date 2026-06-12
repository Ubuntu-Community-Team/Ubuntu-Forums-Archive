---
title: "help!!cannot read anything"
date: 2007-06-13
forum: Desktop Environments
---

### Post by vioakimi on 2007-06-13
I'm a linux newbie! That's important to mention cause it partialy explains panic. 
While trying to install some applications, i apparently made something wrong and now i cannot read anything in my system. All the menus and dialogue boxes are not readable. I can only read texts in my browser -that's why i can still seek help. Any ideas how can i restore my  english language support. I guess this is the proble, Plz help urgently cause i canot work anymore in my thesis!!

---

### Post by almack1 on 2007-06-13
I'm new at this myself and have made some of the same moves. If you haven't got anything you have to keep just re-install and start over. Al Mack

---

### Post by Trueno22 on 2007-06-13
system>preferences>language support should be an icon with flags on it

---

### Post by vioakimi on 2007-06-13
I consider that but the problem is that I will loose some important date -like my emails- which i cannot backup due to the problem. Funny thing is that I guess that it is just a simple library missig but i don't know the exact command to install it through the terminal :(

---

### Post by vioakimi on 2007-06-13
> **Trueno22 said:**
> system>preferences>language support should be an icon with flags on it

Thnks for the tip.
I tried but then i got a message I cannot read.

---

### Post by fdrake on 2007-06-13
it's almost what happens me when i try to open a binary file on the terminal as a text file, after that the terminal acts funny, you see strange characters on the screen. i never had something like that on my desktop environment. my suggestion for you if you cannot use the terminal is to login into a shell (ctrl+alt+F1) and remove the application you installed before.

---

### Post by vioakimi on 2007-06-13
Didn't work either probably because I have some libraries missing and I cannot recover them.

---

### Post by fdrake on 2007-06-13
can you boot in recovery mode from your grub menu?or safe terminal mode when you login?

---

### Post by vioakimi on 2007-06-13
Normally I can. But what should I do after that?

---

### Post by fdrake on 2007-06-13
sudo aptitude reinstall xserver-xorg

---

### Post by vioakimi on 2007-06-14
I found the prblem but i dont know how to resolve it. Problem is I messed up locales settings.

---

### Post by vioakimi on 2007-06-14
no solutio yet. I think im goig to re-install ubuntu

---

