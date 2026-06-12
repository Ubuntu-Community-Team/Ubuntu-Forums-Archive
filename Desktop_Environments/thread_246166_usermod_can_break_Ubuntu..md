---
title: "usermod can break Ubuntu."
date: 2006-08-28
forum: Desktop Environments
---

### Post by Shadyman on 2006-08-28
Scenario: One user, no root, only sudo access. This is the default installation. (Because root is bad ;) )

Action: User uses usermod -G instead of usermod -Ga, and is locked out of everything, including sudo. ](*,) 

Possible Solution: Add a warning prompt when using usermod -G (or even just add it to the usermod man page) 



Is the only solution for getting locked out like that to wipe and reinstall? Should I post this to Malone as 'Wishlist'?

---

### Post by pclogic on 2006-08-28
I did something similar where I forgot the password to my lone sudo user.  The solution is to reboot your computer, and hit Esc to enter the GRUB boot menu.  Select the recovery mode menu item.  You should be logged in as root.

---

### Post by Shadyman on 2006-08-28
D'oh! :-# 

So simple!

Thanks! :mrgreen:

---

### Post by cptnapalm on 2006-08-28
Dear God, man!  This is Unix!  We learn through reflection after shooting ourselves in the foot with large caliber weapons.

Don't feel bad.

Once, when I was root... (can you hear the ominous music beginning?) I was wiping out a bunch of stuff, to free up space, all while flipping between virtual terminals.  And again I moved up a couple of directories, and hit the rm -rf *.  It was about a minute until I realized that I was in the root directory.

I set the thing up to wipe out everything in the entire filesystem.

Two things happened:
1) A reinstall
2) I pay good attention to where I am when removing stuff.

Pain is still the best teacher ;)

---

### Post by Shadyman on 2006-08-28
Great! Now this begs the question, though, what are the default groups that the first user is in? I put myself back into 'admin', and that fixed the sudo problem, but now I am without any group besides myself, admin, and dba (for Oracle XE).

Can anyone do a quick "groups" and tell me what they find?

---

### Post by Shadyman on 2006-08-28
Yeah, I was root once at work, doing normal DBA stuff. I was cleaning up an old Oracle install... And I was in /home/xyz/ and did an 'ls 123', saw that was what I wanted to delete, and did an rm *. I left out the -rf to be "safe". 

My boss was sitting behind me, and said in a rather monotonous, "You just wiped out the xyz home directory." followed by a rather long, awkward pause. :-# 

Then he bursts in, "But that's Ok, there was nothing in there besides directories anyways, and you didn't use -rf". ;) 

After that, I've been rather careful about "looking around" the directory structure first before I rm -rf *  :mrgreen:

---

### Post by funchords on 2006-08-28
> **Shadyman said:**
> Can anyone do a quick "groups" and tell me what they find?

**robb@TOPOL016:~$** groups
robb adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

