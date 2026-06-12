---
title: "Hello!!! help for a nob someone?"
date: 2006-06-23
forum: Desktop Environments
---

### Post by kaky on 2006-06-23
Hi people i am new to linux and also new to ubuntu.
Today i have installed the server version and i was sooo thrilled but my happyness did not last long ...

Instead of an welcome screen (which i supose you should get after booting) i get the black screen with white letters saying that i need to login so i logged in but it says something about "sudo" as admin.. So i write sudo and it says something....
What should i do to get into the normal OS????
(i hope that that black screen is not that normal os](*,)  )

---

### Post by s_h_a_d_o_w_s on 2006-06-23
what did it say? Try loging in again. Maybe unplug your pc, re-plug it and try again. That isn't the normal OS, on't worry. also, if a terminal opens, type sudo su, then your password. 

then try loging in.

---

### Post by Kouya on 2006-06-23
Hmm it sounds like you may have installed the server version of ubuntu and not the desktop version. Check again?

This happened to me when I first tried installing dapper...

---

### Post by kaky on 2006-06-23
yes but i wanted the server version so i can host files on lan network](*,) 

s-h-a-d-o-w-s what do i need to type in again??

---

### Post by art on 2006-06-23
If you installed server version, that's what the OS looks like. You need to install GNOME or KDE desktop environments to get a graphical interface. 
Login with your account name and password, then type 
```
sudo apt-get install ubuntu-desktop
```
the password here is the same as your account password
that will install the GUI.

---

### Post by x64Jimbo on 2006-06-23
The server version is only different from the desktop version in that it doesn't have a GUI. You can host files on the network just fine with the desktop version.

---

### Post by ohgod on 2006-06-23
x64Jimbo is right.  The desktop version is definitely what you want.  You can easily share files with it.

[QUOTE=kaky]yes but i wanted the server version so i can host files on lan network](*,) 

s-h-a-d-o-w-s what do i need to type in again??[/QUOTE]

---

