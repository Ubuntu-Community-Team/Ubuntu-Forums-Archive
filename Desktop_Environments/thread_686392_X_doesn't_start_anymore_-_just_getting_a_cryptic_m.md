---
title: "X doesn't start anymore - just getting a cryptic message"
date: 2008-02-03
forum: Desktop Environments
---

### Post by Sputnik-A on 2008-02-03
Hello World,

I am a Linux-newbie. Just 2 weeks ago I switched to Ubuntu 7.10 and was very pleased with it - until today: I was booting the computer and when X started I got this cryptic message:
[[img]http://img149.imageshack.us/img149/4362/photo0129ci0.th.jpg[/img]](http://img149.imageshack.us/my.php?image=photo0129ci0.jpg) 
(As I am from Germany I usally see latin characers ;) )

Strangely, in the recovery mode X works fine. I even tried reconfiguring X with dpkg-reconfigure xserver-xorg neu but when I restart the computer into the "normal" mode, I again get that cryptic message.

Up until yesterday everything worked and I haven't changed anything in the system yesterday.

Thanks for any help

---

### Post by Andrew Stone on 2008-02-07
Nobody is going to be able to help you since that error box doesn't SAY anything.  Post the results of "cat /var/log/Xorg.0.log" and "cat /var/log/gdm/:0.log" and "cat /var/log/gdm/failsafe.log" and we might figure something out.

---

