---
title: "How To Log In Unix And Use X-windows"
date: 2006-02-14
forum: Desktop Environments
---

### Post by onandon on 2006-02-14
Hi, everyone. I need to log in a unix server to work in x-window environment. In winxp I could use xmanager to log in the unix server and use its x-windows. Then how could I do that in ubuntu? It seems that vnc is just for remote, which means that i have to log in before that.

Could any one help? Thank you.

---

### Post by taurus on 2006-02-14
If you want to log into your server, use ssh.  If you want to be able to display windows on your machine, then use xhost and set environment to export it to your machine!

---

### Post by STRONG05CS on 2006-02-14
HI 

   If u have a LAN then u can do this ...
    
    Press  Ctrl+alt+tab  and ANY ONE function key  (F3 , F4 ,  F6 , F7 , F8 , F9,  try furth....)
    
    root......   something will occur :  type " X -query IP :2 "   IP = internet protocol of the server u r tryn 2 connect 2

    this may work ( or u may replace X with Xserver )

    to open more then 2 desktop just increase 2 to 3 n so on 

:KS

---

