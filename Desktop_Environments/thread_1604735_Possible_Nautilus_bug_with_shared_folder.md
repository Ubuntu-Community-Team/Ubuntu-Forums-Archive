---
title: "Possible Nautilus bug with shared folder?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by coffeecat on 2010-10-24
Using Maverick.

I've just discovered something I've not noticed before in earlier releases. I have samba installed but like to go the easy way when setting up smb shares by right-clicking on a folder and selecting 'Sharing Options' (That, by the way, sets up the configuration for the share in /var/lib/samba/usershares rather than in /etc/samba/smb.conf.)

Trying to get my Mac to be able to access the share, I was trying different modifications to the share with right-click > Sharing Options > Modify Share. Each time I did so, this caused Nautilus to restart - that is, the whole desktop blanked out to just the wallpaper and then my icons slowly reappeared. Worse, a file copy was interrupted. And much worse, a lengthy video encoding using OpenShot was interrupted. Both the latter irretrievably.

This is unfortunate behaviour. Has anyone else seen it? Can anyone else confirm this? I couldn't find anything on Launchpad.

---

### Post by Morbius1 on 2010-10-24
There is a nanosecond of sheer terror when all of a sudden you select create share / modify share and nautilus closes and all the desktop icons disappear. Yep. First noticed it on LinuxMint Debian Edition ( LMDE ) and now Ububntu 10.10.

Since it's also in LMDE I'm guessing it's not an Ubuntu specific bug.

---

### Post by coffeecat on 2010-10-24
Thanks. At least I'm not alone. Must be an upstream problem.

> **Morbius1 said:**
> There is a nanosecond of sheer terror

... followed by several minutes of carpet-chewing rage when you discover your half-encoded video is incomplete and you've wasted a couple of hours. You wouldn't care to modify a share about two hours into a lengthy video encode, would you? Just to be sure it's not just me. :wink:

---

### Post by Morbius1 on 2010-10-24
Did find a bug report though. It implies there is a fix: [https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/655721](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/655721)

---

### Post by coffeecat on 2010-10-24
> **Morbius1 said:**
> Did find a bug report though. It implies there is a fix: [https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/655721](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/655721)

Ah, thanks for that. I've clicked on the me-too button. For me it wasn't just the adding permissions automatically. It happened with other modifications too, although I'm not going to investigate further. At least not while I'm doing any lengthy file operations. :|

---

### Post by chriswhat21 on 2010-10-28
What *is *the fix for this?  Same issue, clicking "Create Share" causes Nautilus crash is 10.10.  I can't find a fix on here or Google.  The bug report just says there's a fix, but not what it is.  A samba update?

---

### Post by ubunterooster on 2010-10-28
> **coffeecat said:**
> Thanks. At least I'm not alone. Must be an upstream problem.



... followed by several minutes of carpet-chewing rage when you discover your half-encoded video is incomplete and you've wasted a couple of hours. You wouldn't care to modify a share about two hours into a lengthy video encode, would you? Just to be sure it's not just me. :wink:
Offtopic but what size video was that to take that long?

---

### Post by coffeecat on 2010-10-28
> **ubunterooster said:**
> Offtopic but what size video was that to take that long?

About 2 hours, but it wasn't the length of the video that was the problem - it was the app I was trying out for the transcoding. And for the life of me I can't remember which one it was now since  I've abandoned it, partly because I was unimpressed by the time it was taking.

The output was just a fairly standard AVI/XVid, which shouldn't take that long. I've settled on DeVeDe for transcoding to AVI now. Nice GUI interface, decent set of options and transcodes in a reasonable time. Yes, that's right - DeVeDe, a DVD authoring app. If you choose the last option in the greeter, it will transcode a video into AVI for you.

---

### Post by coffeecat on 2010-10-28
> **chriswhat21 said:**
> The bug report just says there's a fix, but not what it is.  A samba update?

No, a fix from upstream gnome. Hopefully that will trickle down to Ubuntu sooner or later with a patch for Nautilus, which we'll see in a routine update.

Hopefully. :|

**Edit:** Hmm, strange, but I'm sure I saw the upstream bug report - or perhaps I was dreaming. I can't find it linked on the Launchpad bug. In the meantime the 'fix' is not to be doing anything else when creating or modifying a nautilus share. Nautilus does crash but at least it bounces up again pretty quickly, and it doesn't seem to affect samba sharing.

---

