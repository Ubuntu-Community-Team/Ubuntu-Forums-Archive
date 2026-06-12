---
title: "Install Problems - setting up primary installation repository"
date: 2005-10-13
forum: Desktop Environments
---

### Post by finster on 2005-10-13
Hi all,

I downloaded Breezy this evening and proceeded to get on with installing it.

I'm installing the standard i386 release on an AMD XP2400 (Shuttle barbones PC). Everything seems to work fine up until it is configuring apt, at which point it hangs when "Setting Up Primary Installation Repository". After a few minutes on 25% my PC just switches off. I have tried this twice now with the same results on both tries.

I didn't have any issues with installing Hoary, so I'm a bit stumped - I assume my network driver etc must be supported if it was OK in the previous release.

I have tried logging on to another console (with Alt-F2 etc) but couldn't see anything obviously wrong before my PC powered down.

Anybody got any ideas - I am really keen to get Breezy up and running!

Thanks.

---

### Post by ZenPirate on 2005-10-13
I have the same problem. Completely freezes at 25%.

---

### Post by sig_UVa on 2005-10-14
It did the same thing for me in Hoary.  This [thread ]("http://ubuntuforums.org/showthread.php?t=24775&highlight=installation+primary+repository")(specifically post #8) helped me.

It's not worded the best, but he's basically telling to break the process at some point and then reinitiate it.  Hopefully it will work for ya!

---

### Post by finster on 2005-10-14
[QUOTE=sig_UVa]It did the same thing for me in Hoary.  This [thread ]("http://ubuntuforums.org/showthread.php?t=24775&highlight=installation+primary+repository")(specifically post #8) helped me.[/QUOTE]

Thanks - just tried this and it seemed to work. I pressed [Esc] at the "Add user"  prompt and selected "Install Grub" instead. I then selected adding the user again, at  which point (after adding my user) it went straight to the configuring apt repositories screen. Before I knew it, it had gone past 25% and installed successfully. Don't know if installing grub before conifiguring apt helped or if its a coincidence, but I tried 4 times last night and hit the same problem every time.

Anyway - thanks for the tips - hopefully this will help somebody else in the same position with breezy.

---

### Post by sig_UVa on 2005-10-14
Cool!  Glad it worked!

---

