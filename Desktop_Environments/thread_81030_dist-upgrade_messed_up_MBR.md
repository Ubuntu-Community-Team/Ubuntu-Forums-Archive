---
title: "dist-upgrade messed up MBR??"
date: 2005-10-23
forum: Desktop Environments
---

### Post by WolfJay_83 on 2005-10-23
I attempted to dist-upgrade to breezy and the apt-get just kept quitting half way through, no error message, just returned to prompt.  
So I changed the sources.lst to breezy and tried a apt-get upgrade.  This broke my x-server.  
No big deal I figured, I will just do a clean install from a CD.  After doing that, This is what I get on bootup.
[IMG]http://science.uwaterloo.ca/~jalockli/ash.JPG[/IMG]:confused: 

I re-ran the install cd twice and get the same thing.

hde2 is an ext partition where the root filesystem is.  (hde1 is XP, and hde3 is /home)  Each time that I run the install I remove hde2 and hde3 and re-format them.

The funny (good) thing is, that grub still works and I can still boot into windows.  So, I'm at a loss.

note: I am having trouble figuring out how to do anything in this ash - so instructions may have to include actual commands. 

Any Ideas?

---

