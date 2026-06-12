---
title: "Boot-up time takes 1:40 seconds."
date: 2009-02-17
forum: General Help
---

### Post by cdahmedeh on 2009-02-17
Hello,

In XP, it took less than 1 minute to boot-up. In Ubuntu, it takes 1:40 seconds to start. From Grub to Login it takes 60+ seconds. From Login to Desktop it takes 30+ seconds. Here is the boot chart attached. Also, applications that start after login : Pidgin and Minbar Prayer Times. In addition, I have usplash disabled. What are good tweaks to increase boot-time. I am specially annoyed by the GRUB to Login part which takes a long time.

Thanks

Specifications :
Intel Core 2 Duo T7500 2.2 GHz 4MB
3GB DDR667 RAM
160GB 7200 RPM Drive

---

### Post by handy on 2009-02-17
You can configure grub to start with whatever delay you choose, by editing the menu.lst, it is well worth understanding what you are doing before you start playing with grub:

*_[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)_*

---

### Post by cdahmedeh on 2009-02-17
> **handy said:**
> You can configure grub to start with whatever delay you choose, by editing the menu.lst, it is well worth understanding what you are doing before you start playing with grub:

*_[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)_*

I have the delay set to three seconds. That is not the cause of the slow boot.

---

### Post by Yashiro on 2009-02-17
Try installing 'preload'. The major lag seems to be KDE related.

---

