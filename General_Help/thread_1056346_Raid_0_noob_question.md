---
title: "Raid 0 noob question"
date: 2009-01-31
forum: General Help
---

### Post by whazzzzzup17 on 2009-01-31
Okay I'm trying to multi-boot my new laptop I just bought, Asus G50vt-x1, with windows vista, windows xp,and linux (Ubuntu). However I been reading some other forums and they are saying the only way I can install Windows XP, and maybe Linux (Ubuntu), is if I change/download a Raid 0 driver. 

I am unfamiliar with this "Raid 0" because normally the default is at "1", I believe. Is it safe to change Raid 1 to Raid 0? Can you give me some information on what this is? And most importantly would it damage my laptop. Even though part of it is just a bios setting. 

Any help, I will greatly appreciated it.

---

### Post by Gizenshya on 2009-01-31
here is some info on various RAID configurations.

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

no idea about the other stuff (triple booting those OS's, or changing RAID versions), though

---

### Post by Yashiro on 2009-01-31
Assuming it's laptop and assuming you have only one hard drive,
Switching the raid mode in the bios could invalidate you current HD and render the machine unbootable. 

The driver, if needed, would be a Linux driver and it should not be required to change raid mode to install another OS.

Don't do anything until you've gathered a bit more info.

---

### Post by albinootje on 2009-01-31
> **whazzzzzup17 said:**
> However I been reading some other forums and they are saying the only way I can install Windows XP, and maybe Linux (Ubuntu), is if I change/download a Raid 0 driver. 


Perhaps you're referring to fakeRAID ?
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

