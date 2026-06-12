---
title: "Startup issues"
date: 2009-01-15
forum: General Help
---

### Post by djbushido on 2009-01-15
I'm having problems starting up my ubuntu. for specific information, check this post out [here]("http://ubuntuforums.org/showthread.php?t=1039077"). This gives a detailed overview, and contains logs, etc.

What happens is that normally, a kinit message displays showing "no resume image found, doing normal boot", then X crashes, then i power it off, then it has to check the disk, the check comes back clean, it restarts, then i get a clean startup.

Any ideas on how to fix this?

---

### Post by djbushido on 2009-01-15
EDITEDIT: NOT FIXED!!!

Please see my other posts for both information, and maybe a workaround. Thanks for the help!

---

### Post by wootah on 2009-01-15
> **djbushido said:**
> FIXED!!!
for some reason, X crashed because my filesystem contained errors-maybe in that sector?
Anyway, running fsck from my Fedora dual-boot (thank god i had the idea to do that) fixed it, and I'm back online. SWEET!
 
EDIT: I'd like to mark it solved, but can't get it in the menu. Ideas?
Thread tools at the top right of the forum ?

---

### Post by djbushido on 2009-01-16
Not there (don't ask me where it went...).

Anyway, not actually solved. Fixing the filesystem allowed for one boot, but when I went back, it was messed up again.

I don't know what is happening, besides kinit can't find a resume image (not that I know what that is). My guess is that something is up when the drive shuts down, because it seems that at this point, something gets messed up. Is there a way that I can suspend my drive, writing memory to hard drive, and then power down? That way, my drive stays intact, and i can still boot to windows when my bro needs it.

---

### Post by djbushido on 2009-01-16
Okay, sorry for double post, but this deserves it.

When looking more at my drive, after these errors have occured, i found out that it is mounted read only. Looking in fstab reveals indeed that if there are errors, that it gets mounted read-only.

Don't know what that means, but thought it was important. 

Alsoalso: my drive is a hard disk connected via USB, if that means anything.

---

