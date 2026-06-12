---
title: "Keyboard and mouse don't work at login"
date: 2009-03-06
forum: General Help
---

### Post by yehgross on 2009-03-06
This is my first time using ubuntu so I don't know much. After installing ubuntu, i got to the login screen, but my mouse and keyboard are unresponsive. They usually shut off when ubuntu starts to load and i have no problems using the in Windows Vista. How can I solve this?

---

### Post by murataht on 2009-03-06
what kind of computer you are using? desktop? or laptop? what specs?... which version of ubuntu are you using?

without these informations it is very hard to answer your question.

i will give it a try anyway:

if you are using a laptop, try with a usb keyboard and mouse.

---

### Post by yehgross on 2009-03-06
oops sorry. 
its an Acer m1640desktop:

2ghz intel e2180 dual core processor
2gb RAM
320gb hitachi hdd and running windows vista

The version of ubuntu is 8.10

---

### Post by murataht on 2009-03-06
no problem yehgross. So, it is a desktop...

I am not an expert, but i will give it another try (correct me if I am wrong) . 

this must have something to do with the X, or X configuration file. And a quick googling discovered similar problems...

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254840](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254840)

maybe it is the bug which is affecting your computer. maybe there is a solution somewhere in the post... ( i was not brave enough to read all of the page ).

this seems specific to gnome and gdm. so, if you want, you can try to install kde/kdm or other WM.

or have you tried 8.04? maybe it works for you.

good luck

---

### Post by yehgross on 2009-03-09
Thanks for the help, but i think it was a bug in the installation. Reinstalled and selected US keyboard instead of Canadian and it worked that time.

---

