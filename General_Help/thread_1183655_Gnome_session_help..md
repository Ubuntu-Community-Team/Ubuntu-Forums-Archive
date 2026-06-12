---
title: "Gnome session help."
date: 2009-06-10
forum: General Help
---

### Post by ethoxyethaan on 2009-06-10
Hello, i recently switched from Debian stable to Ubuntu 9.04 to get more up to date software packaging.

Ever since i switched however i had 1 problem, " CTRL-ALT-backspace " will not end my user session, Why is this?

---

### Post by ajgreeny on 2009-06-10
It has been disabled in the newer kernels because, apparently, people occasionally did it by mistake, and so lost whatever they had been working on. I find it very hard to figure out how that would happen, though it seems the use of "sticky keys" can make it do so sometimes when you happen to press those three keys in sequence, not all at once.

You can either get it back with [dontzap]("http://www.google.co.uk/search?q=dontzap&ie=UTF-8") or can just use the alternative Alt Gr+Sys Rq+K which does the same thing, and I suppose is much less likely to be used by mistake even with sticky keys enabled.

---

### Post by ethoxyethaan on 2009-06-10
> **ajgreeny said:**
> It has been disabled in the newer kernels because, apparently, people occasionally did it by mistake, and so lost whatever they had been working on. I find it very hard to figure out how that would happen, though it seems the use of "sticky keys" can make it do so sometimes when you happen to press those three keys in sequence, not all at once.

You can either get it back with [dontzap]("http://www.google.co.uk/search?q=dontzap&ie=UTF-8") or can just use the alternative Alt Gr+Sys Rq+K which does the same thing, and I suppose is much less likely to be used by mistake even with sticky keys enabled.

AltGr + SysRq + K

Pressing sysrq for me just activates a screenshot even if i press the Fn button on my laptop, (so sysRq is not correctly passed). 

But i recall a post on slashdot announcing the zap feature being removed, however by adding 1 line to the Xorg.conf you could enable it again. 
I can't find the post anymore so thanks.

---

### Post by ajgreeny on 2009-06-10
Here it is:  [https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

---

### Post by Hund on 2009-06-10
The package "dontzap" should work to.

Install:

> sudo aptitude install dontzap

Enable/disable:

> sudo dontzap --enable
> sudo dontzap --disable

---

### Post by ethoxyethaan on 2009-06-11
thanks i just edited the xorg.conf file and now everything is working as intended.

Section "ServerFlags"
    Option         "Xinerama" "0"
    Option         "dontzap"  "false"
EndSection

---

