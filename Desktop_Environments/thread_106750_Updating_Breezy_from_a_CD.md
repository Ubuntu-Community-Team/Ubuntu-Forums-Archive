---
title: "Updating Breezy from a CD"
date: 2005-12-21
forum: Desktop Environments
---

### Post by mjshepherd on 2005-12-21
I need to update my recently installed Breezy Badger so i can install various drivers etc., but i only have dial-up internet access from my Ubuntu computer at home.  This means that if I apt-get update it takes about an hour to work out which upgrades I need, and then informs me that it will take 16 hours to download them, and i can't afford the time or the telephone bill!  Is it possible just to download all the possible update files onto a CD using my work (Windows) broadband connection, and run the whole update process using the CD as a repository, both to see which upgrades i need and to install them?

Cheers!

Matthew

---

### Post by frodon on 2005-12-21
All is here : [https://wiki.ubuntu.com/BreezyUpgradeNotes?](https://wiki.ubuntu.com/BreezyUpgradeNotes?)

---

### Post by Irony on 2005-12-21
Yes you can do that - that's how I did it. Follow the notes at;

[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

Read the pre-upgrade and upgrade notes.

---

### Post by mjshepherd on 2005-12-21
But isn't that Wiki about upgrading to Breezy?  I already have Breezy, installed about 4 days ago from a CD. What I need is to update various bits of breezy (apparently), so i can install a gcc-3.4 kernel, then a camera driver.  Also i want to do this with minimal dial-up use, so anything that asks me to apt-get install anything makes me worry that i'm in for another 3 hours of watching things download very slowly!

---

### Post by dcstar on 2005-12-21
[QUOTE=mjshepherd]But isn't that Wiki about upgrading to Breezy?  I already have Breezy, installed about 4 days ago from a CD. What I need is to update various bits of breezy (apparently), so i can install a gcc-3.4 kernel, then a camera driver.  Also i want to do this with minimal dial-up use, so anything that asks me to apt-get install anything makes me worry that i'm in for another 3 hours of watching things download very slowly![/QUOTE]
If you have a Ubuntu PC on a high-speed connection, you can do an update of the packages you want (but you have to specify them) on that system, and then burn the apt cache files to a CD/DVD and copy them to your other PC's apt cache directory.

That should give you the functionality that you want, but it may not be that easy to do!

---

