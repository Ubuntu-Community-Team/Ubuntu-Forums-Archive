---
title: "2 questions on Ubuntu logos"
date: 2006-09-02
forum: Desktop Environments
---

### Post by okok on 2006-09-02
1. When Ubunto or Xubuntu start, while loading the system a logo is displayed, and beneath it some information on what is going on. In other operating systems I saw much more detailed information, usually in text mode. Is this information available also in Ubuntu? Can I make it appear instead of the ubuntu/xubuntu logo and the relatively general information reported there?

2. In Gnome, the main menu comes with an Ubuntu logo. Can this logo be removed or changed, and if so, how?

---

### Post by PathSpace on 2006-09-02
2.  [http://ubuntuforums.org/showthread.php?t=208457](http://ubuntuforums.org/showthread.php?t=208457)

---

### Post by Rui Pais on 2006-09-02
hi, 
1. <-you can disable usplash from boot level or even uninstall it. 

Alternatively you can [try fbsplash]("http://ubuntuforums.org/showthread.php?t=178439&highlight=fbsplash"). 
It allow you to choose if you want a fancy (much better then usplash) boot image with a progress bar and minimal information or see boot messages by press F2 key or set that as default on a configuration file.

---

### Post by okok on 2006-09-02
Thanks for both answers.

Rui Pais, how do I disable usplash or install it?

---

### Post by whizbaby on 2006-09-02
At bootup-time there are more detailed infos on other terminals (I think two and eight) you could access by pressing:

ctrl-alt-[one out of F1 to F8]

If you want to remove it:
sudo apt-get remove usplash (plus evtlly xubuntu-artwork-usplash)

---

### Post by Rui Pais on 2006-09-02
Uninstall it's the easiest way.

If you prefer to disable it, try use an app like **bum** or **sysv-rc-conf** (both in universe repository). 
They allow to enable/disable services that run at boot time.

---

### Post by okok on 2006-09-02
Thanks for all the information!

---

