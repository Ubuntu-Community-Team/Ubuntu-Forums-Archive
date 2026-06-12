---
title: "One menu question &amp; one e17 question"
date: 2006-08-08
forum: Desktop Environments
---

### Post by PathSpace on 2006-08-08
Hi everyone, I recently switched to Ubuntu and am very happy with it.  :D  I have a few questions that some people around here might know the answer to.  

Having previously used various Debian versions, I am familiar with the package "menu."  I was wondering what would happen if I installed this on Ubuntu (since it is available).  Would it mess up the nice GNOME menus Ubuntu has already laid out (the ones you can edit with Alacarte) by replacing them with the Debian menu, or would it just add the Debian menu and leave the rest of the menu alone?

Also, I was curious if anyone has recently installed e17 onto Dapper.  I have seen various repositories one could add and a few installation guides, but am not sure about their relevance because they were quite old.  Does anyone know what the "best" way to put e17 onto a current Dapper system is?

Thanks in advance.  :)

---

### Post by crackseller on 2006-08-08
Installing the debian menu will not mess up your current gnome menu, it will be added as an extra menu (Applications > Debian > ...).

To answer your 2nd question: I have e17 running on ubunutu. I installed it out of curiousity because I was using an earlier version a couple of years ago. I followed the way described in this thread: [http://ubuntuforums.org/showthread.php?t=228018](http://ubuntuforums.org/showthread.php?t=228018). I can't tell you if it is the best way but I can tell you that it is a way that worked for me.

---

### Post by PathSpace on 2006-08-08
Thanks for that; I'll try installing e17 that way.  :) 

Btw, I installed menu, but I do not see any extra Debian menu in my Applications menu.  Do I need to do something extra to enable it?

---

### Post by Rui Pais on 2006-08-08
Hi,
> **PathSpace said:**
> Thanks for that; I'll try installing e17 that way.  :) 
may i suggest [this thead]("http://ubuntuforums.org/showthread.php?t=97199"). 
It's based on a script by Morlenxus, the main mantainer of [get-e]("http://www.get-e.org") site and so someone deep involved on e17 development.

For me it's the best installation method. 
(Edit: Because it installs on /opt/ and not mixed with you /usr system, simple to backup and clean. It's plain cvs so always uptodate and very distro independent. It's very flexible, allowing a simple way to choose which apps to install by editing a config file. The thread also gives a miriad of solutions to several problems that could happen :))
 

> 
Btw, I installed menu, but I do not see any extra Debian menu in my Applications menu.  Do I need to do something extra to enable it?
Try to make it visible with alacarte.

hope that helps

---

### Post by crackseller on 2006-08-08
Actually you don't. Might help to restart the gnome panels:
```
killall gnome-panel
```

Here a screeny, in case you want see it in action:
[http://img505.imageshack.us/img505/142/screenshotzl7.jpg](http://img505.imageshack.us/img505/142/screenshotzl7.jpg)

---

### Post by PathSpace on 2006-08-08
No luck on the menus, but...e17 worked great!!  Thanks!  :D

---

