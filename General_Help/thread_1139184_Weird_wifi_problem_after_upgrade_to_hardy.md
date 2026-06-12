---
title: "Weird wifi problem after upgrade to hardy"
date: 2009-04-26
forum: General Help
---

### Post by shelbyvision on 2009-04-26
I finally got my computer upgraded from gutsy to hardy (see [http://ubuntuforums.org/showthread.php?t=1135276&highlight=shelbyvision]("http://ubuntuforums.org/showthread.php?t=1135276&highlight=shelbyvision")). Now I have a couple strange problems, I don't know if they are related. 
First, when I try to shut down or restart, it hangs on shutdown with a black screen with several lines of text ending with:
*Starting TiMidity++ ALSA midi emulation     [OK]
-(blinking)
So then the only way I can shut it down is to hold down the on-off button for several seconds. 
Second, if I shut down or restart, there is no internet connection either with wifi or ethernet. The only way I've been able to connect is to take the wifi card out, restart the computer, and then put the card back in after everything is up and running. Very annoying. 
Any suggestions for a fix for these problems will be appreciated.

---

### Post by shelbyvision on 2009-04-27
bump

---

### Post by shelbyvision on 2009-04-28
Still no reply...

---

### Post by freonchill on 2009-04-28
quick and nasty answer is backup and do a clean install of hardy

---

### Post by shelbyvision on 2009-04-28
> **freonchill said:**
> quick and nasty answer is backup and do a clean install of hardy

No thanks. It took 7 hours to do the install I have. Nasty, yes, quick, no.
I only shut it down or restart it once a week at most, so I'll put up with the problem until I can get a good fix.

---

### Post by Yashiro on 2009-04-28
> It took 7 hours to do the install I have.
Wow.

---

### Post by shelbyvision on 2009-04-29
It occurred to me that my wifi card, a US Robotics MAXg, is one of those that requires ndiswrapper in order to work. I did a little research and found that there is a compatibility problem with ndiswrapper and Linux kernel 2.6.24. So I tried booting up using the grub menu option "Ubuntu 8.04.2, kernel 2.6.22-16-generic" and the problem disappeared. Now I'm wondering, am I going to run into problems if I use the older kernel? Also, is there an actual fix for this problem? :confused:

---

