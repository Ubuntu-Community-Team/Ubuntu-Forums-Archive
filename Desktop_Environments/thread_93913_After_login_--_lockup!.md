---
title: "After login -- lockup!"
date: 2005-11-23
forum: Desktop Environments
---

### Post by petri on 2005-11-23
Actually I get the login and after I have logged in the screen flickers once and the mouse arrow disappears. Then the screen is just brown.

If I chance in login pagen to "failsafe gnome" it (OS) continues startting and I get access, for example I'm writing this. But what shall I do now?

At the very beginning when I hit the Esc I can see that OS probes for IRQ for "hdc" and "hdd" which I don't have. I have just one hd and a dvd (hda, hdb).

I'm just about giving it upp with "the crashfree linux" so please help...

---

### Post by 23meg on 2005-11-23
Do you have Nvidia video hardware? If so, follow these steps:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#installnvidiadriver](http://help.ubuntu.com/starterguide/C/faqguide-all.html#installnvidiadriver)

---

### Post by petri on 2005-11-23
nope
ofcourse  I forget to add my specs... sorry

asus a7v-266e
xp1800+
ati radeon 8500dv aiw

I got these when I typed: cat /var/log/Xorg.0.log | less

(EE) Unable to find a valid framebuffer device
(EE) RADEON(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
        (you may have to look at the server log to see warnings)
(WW) RADEON(0): fbdevHWInit failed, not using framebuffer device

what do they mean? as you can see I'm not so good at this.

I have tried: sudo dpkg-reconfigure xserver-xorg
did not help... or maybe I don't know how to use it :(

---

### Post by petri on 2005-11-25
can anyone help me?

---

### Post by taurus on 2005-11-25
What does your /etc/X11/xorg.conf look like?

more /etc/X11/xorg.conf

---

