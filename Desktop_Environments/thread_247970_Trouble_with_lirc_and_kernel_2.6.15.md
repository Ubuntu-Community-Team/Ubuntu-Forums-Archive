---
title: "Trouble with lirc and kernel 2.6.15"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Azathoth_ on 2006-08-31
Hello! It's my first post with this account.
I have problems to execute Lirc on my TV Capturer (KWorld DVB-T 100 wiith Conexant 2388x chipset) and cannot configure Lirc, but I can compile Lirc
All the steps I do are "correct" but when I try
& sudo modprobe lirc_gpio
a error appears, and cannot add this module, and then I cannot execute Lirc.
I have searched a lot of time about configuration of Lirc for this Tv card and no results.
I can watch TV with kaffeine.
I use Ubuntu Dapper 6.06 with Gnome and Xgl.
Thanks
Mario

---

### Post by ceargle on 2006-08-31
I'll second your complaint, I was using the lirc_i2c module in Xubuntu with my bttv card until updating to the 2.6.15-26-686 kernel.  Tried recompiling, and received an error saying the module could not be inserted.

Edit: This thread should probably be moved to the hardware help forum.

---

### Post by Azathoth_ on 2006-08-31
Any suggestion?

---

### Post by Azathoth_ on 2006-08-31
Anyone can help us?

---

### Post by tlue on 2006-09-16
> **Azathoth_ said:**
> Anyone can help us?
See this thread [http://www.ubuntuforums.org/showthread.php?t=188381](http://www.ubuntuforums.org/showthread.php?t=188381)
and therefore surf to
[http://www2.truman.edu/~dat725/htpc_single.html#htpc6](http://www2.truman.edu/~dat725/htpc_single.html#htpc6)
This worked for me. Before that I couldn't load my compiled modules because i didn't have the correct links for the build-environment.

---

