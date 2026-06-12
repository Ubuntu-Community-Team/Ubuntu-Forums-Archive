---
title: "command past boot screen?????"
date: 2005-09-09
forum: Desktop Environments
---

### Post by gerrenj on 2005-09-09
I just installed UBUNTU.  On the boot screen, I put in my id and password, but how do I get pass that point.  What command opens UBUNTU?  Please help; I am ready to see what this OS is all about.

---

### Post by iimess on 2005-09-09
[QUOTE=][/QUOTE]
 maybe a "sudo startx" or ctrl+alt+f7?

---

### Post by amohanty on 2005-09-09
So you enter the username, press enter, you enter the password and press enter... what happens next?

AM

---

### Post by professor_chaos on 2005-09-10
That should be all you need to do. 

To check error messages try 
```

Ctrl+Alt+F1
```

then login from the command prompt.

then type

```
startx
```

what do you see?

---

### Post by gerrenj on 2005-09-10
Thank you for responding.  I tried to enter startx, but nothing happened.  The browser just blinks as if I need to do something else.  I called this local computer shop and they told me that UBUNTU may not reconize my video card.  I have an NVIDIA card installed.  I am very green with Linux.  Is there another version of Linux that maybe easier, then maybe try UBUNTU later?  Thanks in advance.

---

### Post by professor_chaos on 2005-09-11
Nvidia is well supported by Ubuntu. Don't give up too fast, if you solve your problem your likely to learn a lot while doing so. 

It would be nice if you could post any error messages you get. To get a list type "dmesg"

once you log on via the command line you can reconfigure your graphical server by typing "sudo dpkg-reconfigure xserver-xorg"

That should take care of any errors in your configuration. However it is likely that that won't fix your problem and you may want to change your driver setting from "nvidia" to "nv". Then what happens? You can do this from the command line or when reconfiguring your graphical server.

There are a lot of distributions out there that may work better for you. Linspire, SUSE, mandrake. I choose Ubuntu over all.

---

