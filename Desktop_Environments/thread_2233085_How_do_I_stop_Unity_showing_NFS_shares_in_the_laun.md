---
title: "How do I stop Unity showing NFS shares in the launcher?"
date: 2014-07-06
forum: Desktop Environments
---

### Post by Carl H on 2014-07-06
I have about half a dozen NFS shares mapped to my Ubuntu14.04 box. Each one of them shows up as an icon in the Unity Launcher. This is unnecessary and annoying - they take up a fair bit of space, and in any case I only need them to be visible from Nautilus, which they are. 

Right clicking and 'unlock from Launcher' gets rid of them. But they come back the next time I log on, or if I remount them. 

Is it possible to stop them appearing in the launcher ever? 

More generally.... is it possible to configure exactly what shows up in the launcher?

---

### Post by mc4man on 2014-07-06
The current crappy system Ubuntu has in place amounts to a blacklist only,  based on device uuid.
I know nothing about nfs shares - do they have their own uuid's?

You could see what's up by logging in (all shares showing). Pick 1 & 'unlock from launcher'. Then open dconf-editor > com > canonical > unity > devices & see what's entered in the blacklist for the share you just removed.
Then log out/in, remove the very same share again. Check & see if it's in the blacklist the exact same as before or does it get a new entry?

---

### Post by Carl H on 2014-07-09
NFS shares don't have UUIDs, but this problem is now the least of my problems with Ubuntu14.04.  I've had to resort to typing this from my Linux Mint box...

---

### Post by Carl H on 2014-07-12
> **mc4man said:**
> 
You could see what's up by logging in (all shares showing). Pick 1 & 'unlock from launcher'. Then open dconf-editor > com > canonical > unity > devices & see what's entered in the blacklist for the share you just removed.
Then log out/in, remove the very same share again. Check & see if it's in the blacklist the exact same as before or does it get a new entry?

It's the same entry, but after removing the share again, the entry has '-' added to the end of it.

---

