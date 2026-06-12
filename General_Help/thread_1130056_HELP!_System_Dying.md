---
title: "HELP! System Dying"
date: 2009-04-19
forum: General Help
---

### Post by suda on 2009-04-19
It started with a video transfer. I got a message that _**device/file space all used up**_ (tried to use screen shot for this but screen shot wasn't working). Then I tried to get into Synaptic Manager--said I didn't have permission. Tried to run screen shot--but that didn't work. I copied what Synaptic said:

Failed to run/usr/sbin/synaptic as a user root
Unable to copy user's Xauthorization file

I lost all my bookmarks in Firefox--it's acting up.

What's going on? Please help!!

---

### Post by LiamWilson on 2009-04-19
Sounds like you have used up all the space on your Hard Drive, so by deleting your bookmarks, it's trying to make space. Try running this in a terminal:
```
sudo apt-get clean
```

Also try moving some of your files/folders in your home folder to an external storage medium, such as a CD/DVD, USB drive, or a Zip/FLoppy drive.

---

### Post by suda on 2009-04-19
> **LiamWilson said:**
> Sounds like you have used up all the space on your Hard Drive, so by deleting your bookmarks, it's trying to make space. Try running this in a terminal:
```
sudo apt-get clean
```

Also try moving some of your files/folders in your home folder to an external storage medium, such as a CD/DVD, USB drive, or a Zip/FLoppy drive.

I'm writing this on the Windows side, Mr. Wilson. Thank you for your reply--but now I can't even boot up Ubuntu, so I'm going to do a Wubi reinstall and start over. Seems the only option. I almost didn't get into Windows...

---

### Post by LiamWilson on 2009-04-19
Hmm. Very, very strange. What size hard disk space did you give it last time?

---

### Post by suda on 2009-04-20
> **LiamWilson said:**
> Hmm. Very, very strange. What size hard disk space did you give it last time?

I gave the original install 8 GB, but when I reinstalled, I upped it to 15 GB. I also found some workarounds in Launchpad that also address this issue, so if this happens again, I'll know what to do. Thanks again!

By the way, since we're sort of on this subject, how can I tell how much space is left on my partition? Is there a GUI or something that can tell you this?

---

