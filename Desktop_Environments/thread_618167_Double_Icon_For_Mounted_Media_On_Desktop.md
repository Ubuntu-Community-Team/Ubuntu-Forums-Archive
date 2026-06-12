---
title: "Double Icon For Mounted Media On Desktop"
date: 2007-11-20
forum: Desktop Environments
---

### Post by AegisTalons on 2007-11-20
On the desktop, I get double icons for pretty much my removable media. This doesn't happen with hard drives, but it does happen with USB, IPOD, CD/DVDs. Using the USB as an example, when the USB is in the computer, there are two icons displayed on the desktop. When I unmount the USB, one icon disappears and it is fine to take out the USB. Yet, the other icon is still displayed but it doesn't do anything. 

Anyone have any ideas what is going on here? Any help is greatly appreciated.

---

### Post by abdulquadir on 2007-11-20
i am alos facing same problem is it some kind of a bug which needs to be fixed

---

### Post by Subban on 2007-11-20
Same problem here, only seemed to have started over the weekend for me, or at least its the first I noticed it.

Edit: Did a reboot to silicon oil a noisy fan and the extra icons have gone, would still like to konw what caused it and fix it however.

---

### Post by Subban on 2007-11-23
Forgive the double post, but I felt after 3 days it wouldn't hurt and the OP is more likely to get an alert of a post if he is subscribed to the thread.

Still happening, what I do now is unplug the offending usb item, then open a terminal and do:
```
killall nautilus
```

Nautilus will reload itself and then you can plug the usb thing back in, without the double icon. Would still prefer a 'proper' fix.

---

### Post by derby007 on 2007-11-24
I have the same problem, it happens to my External USB drive.

---

### Post by rune0077 on 2007-11-24
This also happens to me. It seems to be happening when you shutdown with the device plugged in, and then boot up again without removing it.

For instance: if I remember to unmount my iPod before I shutdown, nothing strange happens. However, if I forget to do it, then my iPod will still appear as being mounted during next startup, even if it isn't plugged in. If I then plug it in, I have two iPod icons.

---

### Post by rushmobius on 2007-11-24
This happens for me as well, though I don't have any USB drives mounted.

Out of my 2 DVD drives, the one with a disk in it occasionally shows up twice on my desktop. It seems fairly random at startup.

---

### Post by Tsume on 2007-11-25
Same problem here.  I'm running Linux Mint 4.0 but it's essentially the same thing...  Almost always happens in my 160gig external drive.

Will not happen if I connect after I'm all booted up.

---

### Post by eg0n on 2007-11-28
> **rune0077 said:**
> This also happens to me. It seems to be happening when you shutdown with the device plugged in, and then boot up again without removing it.

Same problem. Every time I boot up with my usb drive already plugged in I have a second icon. I can use both of them but when I select to unmount one, the one left is unusable. I think that before gutsy it didn't happen . Is there anyone with a previous distro who has that problem?

---

### Post by Subban on 2007-11-28
> **eg0n said:**
> Same problem. Every time I boot up with my usb drive already plugged in I have a second icon. I can use both of them but when I select to unmount one, the one left is unusable. I think that before gutsy it didn't happen 

It certainly didn't happen here with Feisty, only started when I did a (clean) install of gutsy.

---

### Post by atlas95 on 2007-11-28
Same problem here with external harddrive,plug-in while shutdown and restart....sometimes

---

