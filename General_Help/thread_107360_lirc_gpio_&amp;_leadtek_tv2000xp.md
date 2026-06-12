---
title: "lirc_gpio &amp; leadtek tv2000xp"
date: 2005-12-22
forum: General Help
---

### Post by sagerion on 2005-12-22
I have successfully followed [http://www.ubuntuforums.org/showthread.php?t=30612&highlight=lirc](http://www.ubuntuforums.org/showthread.php?t=30612&highlight=lirc) up to step 13 with out any errors.  

When I go to install lirc & lirc-x I get a message saying "I couldn't load the required kernel modules You should install lirc-modules-source to build kernel support for your hardware"

I have also attempted to "modprobe lirc_gpio" I get a FATAL Error and ot says Invalid request code.

Anyone got any ideas where I went wrong?

---

### Post by Azathoth_ on 2006-08-31
I am in the same situation. I have the same problem and nobody helps me...

---

### Post by Xappe on 2006-09-08
i would install the linux-headers package for your running kernel (uname -r to find out), and relink /usr/src/linux to the headers instead of the linux source.

Then recompile lirc and it should work.

(installed lirc 0.8.0 two days ago and it works for both my ir-recievers)

---

