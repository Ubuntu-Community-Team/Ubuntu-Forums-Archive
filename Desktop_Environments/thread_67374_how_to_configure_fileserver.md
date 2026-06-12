---
title: "how to configure fileserver"
date: 2005-09-20
forum: Desktop Environments
---

### Post by tram200050 on 2005-09-20
hi, i am new to ubuntu, the desktop is now configure and i would like to configure the computer to be a fileserver, 
where to start, can somebody help, PLEASE

thanks in advance

---

### Post by jworr on 2005-09-20
If you are sharing files with a windows computer you will need samba,

however if you are sharing files between linux computers and you don't care too much about speed and you want something 99.9% reliable use ssh

I'll show you how to configure samba because it works for everything

first you need to install the samba server, ubuntu only comes with the client installed

goto gnome menu => System => Administration => Synaptic
search for samba and install it

next we need to configure it

goto 

gnome menu => System => Administration => Shared Folders

there you can create shares and users

---

### Post by tram200050 on 2005-09-20
thanks, now i have this
1, samba installed successfully
2, shared a folder
 and what i dont know is how can i access and log my windows into UBUNTU, is there another added app to be installed?

big thanks to your reply ](*,)

---

### Post by jworr on 2005-09-22
You need to create users for those shares, you can do that in the same place where you setup your shares

gnome main menu => System => Administration => Shared Folders

make a user and set him as the only one who can use the share if you make it as exactly what your windows user name and password is then it should log you in automatically

---

