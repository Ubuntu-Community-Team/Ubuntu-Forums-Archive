---
title: "Usplash disappears in boot if no swap"
date: 2009-01-16
forum: General Help
---

### Post by maddis on 2009-01-16
I'm using Ubuntu in embedded pc and in normal operation it doesn't have swap in use since it uses CF-card. 

I noticed that splash-screen disappears in startup. I have my own custom usplash-theme, but same happen with usplash-theme installed from Ubuntu repositories(I haven't check with the original ubuntu-usplash theme though).

When starting without swap the normal left/right bar is shown, but when the progress bar should start to grow, the screen is switched to text mode and boot texts are shown instead of splash-screen. 

If I make even a 10MB swap-partition and use, there is no problem. The unit itself has 1GB of RAM so it doesn't need swap to operate and with 10MB swap there is zero byte used after startup. Something just need swap to be there.

The problem is 'solved' now with that 10MB swap-partition and then I disable it in rc.local after the system has started to get swapless operation. 

I'm just interested to know if someone else has discovered same feature and what is the right way to fix it.

---

### Post by dcstar on 2009-01-16
> **maddis said:**
> I'm using Ubuntu in embedded pc and in normal operation it doesn't have swap in use since it uses CF-card. 
.........
I'm just interested to know if someone else has discovered same feature and what is the right way to fix it.

You may want to see how the ubuntu-eee people have done it as they don't seem to have swap but I still see the splash screen.

As well, you may want to do an ```
update-initramfs -k all
``` to see if that changes things.

---

### Post by maddis on 2009-01-16
When I install my own splash-screen I run in the postinstall - script command: update-initramfs -u -k all

That doesn't change the behavior in swapless operation.

I'll look into that ubuntu-eee and see if I can find how they have done it.

---

### Post by elicn on 2009-05-09
It seems that a few steps can solve that thing up:

[LIST]
[*]Remove redundant swap entry (if exists) from /etc/fstab
[*]Remove 'resume' swap entry from /etc/initramfs-tools/conf.d/resume
[*]Perform update
[/LIST]
```
sudo nano /etc/fstab
sudo nano /etc/initramfs-tools/conf.d/resume
sudo update-initramfs -u
```
Hope it helps

---

