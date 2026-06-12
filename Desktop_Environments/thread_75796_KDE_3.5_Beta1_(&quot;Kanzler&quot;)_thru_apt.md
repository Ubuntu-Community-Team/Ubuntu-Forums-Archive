---
title: "KDE 3.5 Beta1 (&quot;Kanzler&quot;) thru apt ?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by i-x on 2005-10-14
Hello,

Is there any way i can configure my /etc/apt/sources.list so I can install KDE 3.5 Beta1 ("Kanzler") via apt ?

I've tried several things on my own but didn't manage it to work. Also tried to find information on google but couldn't find anything. Seem to be an awful lot of point and clicking downloading it via Firefox.

Thanks in advance.

---

### Post by Knome_fan on 2005-10-14
[http://www.kubuntu.org/announcements/kde-35beta1.php](http://www.kubuntu.org/announcements/kde-35beta1.php)

Just follow the instructions there.

Have fun!

---

### Post by i-x on 2005-10-14
It might be possible that still not had enough coffee today because I can't figure out what packages to install. What should I write after apt-get install ? (Note that I commented out *everything* in my sources.list except the sources found on above mentioned page.)

Sorry to be such pain for a n00b, but one day I hope to be skilled enough to contribute myself to this forum. :)

---

### Post by manubreizh on 2005-10-14
hi, you can do it by several ways : - you have synaptic, you have added the source package address (deb [http://kubuntu.org/kde35beta1](http://kubuntu.org/kde35beta1) breezy main), just refresh packages info and see what's ready for upgrade ; - you have adept, and the way is similar (in adept you add the adress, and adept updates manager tells you what is ready to upgrade, click go and it's done) ; - you want to do it from konsole, then you have already edited /etc/apt/sources.list , added deb [http://kubuntu.org/kde35beta1](http://kubuntu.org/kde35beta1) breezy main , then i think an apt-get update and apt-get dist-upgrade should work, but some users more advanced in kubuntu should be more precise to thaht point. as far as i m concerned, i'll try with synaptic in a minute and add comments there after see u soon

so i've done like written above with synaptic, and all kde stuff appears to be upragable to 3.5beta1 ; so it seems to work
i hope it helped

---

