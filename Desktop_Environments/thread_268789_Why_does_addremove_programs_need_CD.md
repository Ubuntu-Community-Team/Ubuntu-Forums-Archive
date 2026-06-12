---
title: "Why does add/remove programs need CD?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by wkulecz on 2006-09-30
Just did an alternate install.  Things went smoothly until I tried to install some extra packages with "Add/Remove".  Files started downloading, then it asked for my CD, put it in pressed OK and now it continues to nag!

What's up with this?  Didn't have this problem with other systems I'd setup from the live CD.

Solution?

--wally.

---

### Post by aysiu on 2006-09-30
Next time, click **Advanced**

This will change to Synaptic Package Manager.

Then click **Settings** > **Repositories**

Uncheck (or untick) the CD-ROM source. **Close**.

Then click **Reload**.

---

### Post by wkulecz on 2006-10-01
Yes that seems to have been it,  Curious why the live installer didn't default to looking on the CD.

--wally.

---

### Post by toolman59 on 2007-11-15
I have the opposite problem on FF7.04 it always asks for an Internet connection.  Add/Remove progs dialog box has a Preferences button instead of Advanced, however, when the Preferences dialog opens I uncheck the all the Internet options and check the cdrom box, even so it still wants an Internet connection when I run the Add/Remove progs.  Checking back to Preferences I find that one of the Internet connections has been ticked again.  At the moment I don't have an Internet connection until I can load Netgear drivers.

Any help would be most welcome.

toolman59

---

### Post by louieb on 2007-11-15
> **wkulecz said:**
> ..Curious why the live installer didn't default to looking on the CD...

> **toolman59 said:**
> I have the opposite problem on FF7.04 it always asks for an Internet connection....

The live CD doesn't have a repository built  in.  Not enough room.

The alternate CD  has a built in repository.  It has some room left over after the installer. So that CD has a small repository containing the more popular software packages.

---

### Post by toolman59 on 2007-11-16
Thank you

toolman59

---

