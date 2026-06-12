---
title: "Problem with Kde autostart"
date: 2007-02-03
forum: Desktop Environments
---

### Post by geco on 2007-02-03
Hello,
I am on Kubuntu 6.06 running kde 3.5.5
After I dist-upgraded I experienced problems with ksmserver. I use a text login and then, if I need it, I start X server with startx.
We I logged out from KDE, the ksmserver crashed so I removed and reinstalled it.
Now KDE does not execute anymore the scripts I have in my Autostart directory. :confused: 
I searched around ubuntuforums and I found only this useless post: [http://ubuntuforums.org/showthread.php?t=341910&highlight=kd+autostart+problem](http://ubuntuforums.org/showthread.php?t=341910&highlight=kd+autostart+problem) :(
Does anyone have any suggestion???

byebye
Geco

---

### Post by geco on 2007-02-04
UP

...still no suggestions????

---

### Post by g8m on 2007-02-05
Weird.

Any errors in ~/.xsession-errors or in /var/log/Xorg.0.log or dmesg?

---

### Post by geco on 2007-02-05
> **g8m said:**
> Weird.

Any errors in ~/.xsession-errors or in /var/log/Xorg.0.log or dmesg?

I have no dmesg errors.
Actually I didn't check ~/.xsession-errors and /var/log/Xorg.0.log :oops:
I'm not on my computer now, I will check them later.

Thanks

---

### Post by geco on 2007-02-07
> **g8m said:**
> Weird.

Any errors in ~/.xsession-errors or in /var/log/Xorg.0.log or dmesg?

files checked... no errors...

any suggestion?

---

### Post by geco on 2007-02-09
problem solved.
actually i don't know very well what happened, but it seems I solved my problem.

I *downgraded* the **kdebase-kio-plugins** package (and consequently all the dependencies) and then I upgraded... and autostart works.

Anyway I **don't** suggest this method that is too "random" ;)

---

