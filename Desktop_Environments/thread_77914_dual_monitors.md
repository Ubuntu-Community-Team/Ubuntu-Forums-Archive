---
title: "dual monitors"
date: 2005-10-17
forum: Desktop Environments
---

### Post by npodges on 2005-10-17
is it possible to use dual monitors for my desktop in ubuntu? when i have it set up currently, it just shows the same image on both. (both come from the same video card) also, can i make it show two different desktops, one per monitor?
thanks

---

### Post by Stormy Eyes on 2005-10-17
I don't quite understand your question. Have you already installed Ubuntu? It is possible to do dual-monitor setups in Ubuntu, as in any Linux, but it requires tweaking of the X Window System's config file. I can help you with that if you give me more info.

---

### Post by kANDIs on 2005-10-17
Hi!

I also tried to set up a second monitor on my notebook and already posted it in another thread ( [http://www.ubuntuforums.org/showthread.php?t=31686&page=3](http://www.ubuntuforums.org/showthread.php?t=31686&page=3) ), but got no answer yet.
Maybe you can help me?
Thanks,
Andi

---

### Post by Stormy Eyes on 2005-10-17
[QUOTE=kANDIs]Hi!

I also tried to set up a second monitor on my notebook and already posted it in another thread ( [http://www.ubuntuforums.org/showthread.php?t=31686&page=3](http://www.ubuntuforums.org/showthread.php?t=31686&page=3) ), but got no answer yet.
Maybe you can help me?
Thanks,
Andi[/QUOTE]

It looks like you have a Xinerama-style setup, but you've disabled Xinerama. Try changing **Option "Xinerama" "Off"** to **Option "Xinerama" "On"**. I'll cross-post this in the other thread, OK?

---

### Post by kANDIs on 2005-10-17
No, sorry
same error

---

### Post by jonesy on 2005-10-17
Are you using the NVIDIA binary drivers, or is it a non-NVIDIA setup?

---

### Post by kANDIs on 2005-10-17
it's an non nvidia
should be a via. at least the scanpci says so
in the xorg.conf I'm using the vesa driver, because it was also used in the original xorg.conf

---

### Post by jonesy on 2005-10-17
I've never had to do it on a non-nvidia setup, but there are TONS of how-tos for setting up dual monitors in X.  Try this one: [http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors).  Or google for some others.  I'd help if I could.  I'd recommend against running any more auto-configuration utilities if they say to though, just add the lines that define your screen layout and you should be good to go.

---

### Post by kANDIs on 2005-10-17
googling wasn't a great help till now. I've tried it before without working results
but I'll still have a look at that How-To
thanks anyway

---

