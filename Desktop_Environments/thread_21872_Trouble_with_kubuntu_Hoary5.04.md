---
title: "Trouble with kubuntu Hoary5.04"
date: 2005-03-24
forum: Desktop Environments
---

### Post by swatch123 on 2005-03-24
I downloaded Kubuntu hoary 5.04 (2.6.10-4)and installed yesterday.I find there are some problems in this distribution.
  1  usbhd drive read/write unormal(my debian with 2.6.10-1-686 kernel runs very well).
  2. no buttons on kde x app progs
  3  no filemanager. 
  4  root can't login at tty.a user instead of root when u first into kde,root   is disble .I deleted root and add root again,then root can be used.

---

### Post by lao_V on 2005-03-24
[QUOTE=swatch123]
 4 root can't login at tty.a user instead of root when u first into kde,root is disble .I deleted root and add root again,then root can be used.[/QUOTE]

Be default, root is disabled in (k)ubuntu!! You need to use sudo

---

### Post by swatch123 on 2005-03-24
sure,but root passwd should be edited and enable by the usr (first into kde),I can't edit root effectively.

---

### Post by techlord on 2005-03-24
to change root's password all you have to do is in a konsole session issue 
sudo passwd root, then set root's password to what ever you want.

---

### Post by swatch123 on 2005-03-24
this is a good way.thanks :D

---

### Post by niti on 2005-03-25
[QUOTE=techlord]to change root's password all you have to do is in a konsole session issue 
sudo passwd root, then set root's password to what ever you want.[/QUOTE]


I tried this and wrote *root* at password but konsole said me that the following 
kemal@kubuntu:~$ su
Password:
su: Authentication failure
sorry.

or other command's result:
kemal@kubuntu:~$ sudo root
Password:
Sorry, try again.
Password:
Sorry, try again.


Nevertheless, I dont understand why root account is disable in kubuntu. Why?

---

### Post by niti on 2005-03-25
I wrote the following command in konsole, and I could update the root pasword. Thanks...

sudo passwd root


But I could not login as root into KDE. How will do it ?

---

### Post by segrewb on 2005-03-25
Follow this link [here](http://www.ubuntulinux.org/wiki/RootSudo) .  It has alot of info on user root login, etc.

---

