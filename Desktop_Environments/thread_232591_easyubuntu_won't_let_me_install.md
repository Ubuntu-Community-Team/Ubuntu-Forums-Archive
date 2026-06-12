---
title: "easyubuntu won't let me install"
date: 2006-08-08
forum: Desktop Environments
---

### Post by majkmil on 2006-08-08
When I try to run easyubuntu with sudo it tells me to run as user. when I do it does not ask for a password and then says permission denied to /var/lib/dpkg. I tried to change permissions in dpkg directory but I used chmod -r, and now I can't even acces the directory. Can I change permission to this folder so easyubuntu will run? I don't understand why easyubuntu does'nt ask for a password.  Thanks for any help

---

### Post by computergroove on 2006-08-08
I would use a live cd to do it. I had a similar problem and I was able to reset permissions by using knoppix to reset the folder permissions. The ubuntu 6.06 install cd should work just as well.

---

### Post by someguyouknow on 2006-08-08
are you running as root?.....
if so, change to user and it should be fine.....

---

### Post by majkmil on 2006-08-09
I tried running as user and it says when asked for a password at the prompt but does not ask for one. Only tries to run and I get the permissins error. I finally got automatix to run and now I have video in konqueror but when I try in firefox I get the stop buffering error in sites like nfl.com. I had this before in gnome and I forgot how I resolved this. Can you tell me how to change the permission back to default for /var/lib/dpkg?   Thanks for your help

---

