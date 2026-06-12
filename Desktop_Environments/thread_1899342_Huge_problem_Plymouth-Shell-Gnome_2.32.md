---
title: "Huge problem Plymouth-Shell-Gnome 2.32"
date: 2011-12-23
forum: Desktop Environments
---

### Post by EmmeVi on 2011-12-23
Hi!
 
I have a huge problem: my loved 10.10 had problems on seeing the plymouth "Ubuntu Logo", the problem appeared few days ago: opening the PC, the first seconds after booting showed some shell sentences (white on black screen), but after that I had the normal gdm login screen.
So I followed this guide to make plymouth go:
 
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
 
However now I can see the Ubuntu Logo but gnome can't start: I have the login screen in shell form (white words on black screen), and after logging it appears the "terminal-like"[COLOR=black]xxxx@xxx :$[/COLOR]
 
What can I do? :confused:
 
Thx

---

### Post by BC59 on 2011-12-23
Push ALT+CTRL+F1 and enter your logon name and password.
Then try to undo the changes, run
```
gksu gedit /etc/default/grub
```

then restore the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and delete all the "quiet splash [COLOR="Blue"]nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap[/COLOR]"

Then push CTRL+X and reboot

---

### Post by EmmeVi on 2011-12-24
> **BC59 said:**
> Push ALT+CTRL+F1 and enter your logon name and password.
Then try to undo the changes, run
```
gksu gedit /etc/default/grub
```

then restore the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and delete all the "quiet splash [COLOR="Blue"]nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap[/COLOR]"

Then push CTRL+X and reboot

Thank you, BC59, your answer was really useful!:D

Merry Christmas to you and to the whole community!:KS

---

### Post by BC59 on 2011-12-24
Merry Christmas to you and all the best!

---

