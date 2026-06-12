---
title: "cd in drives causes pc to freeze"
date: 2006-06-07
forum: Desktop Environments
---

### Post by veloxdraco on 2006-06-07
whenever i put a cd in my dvd-rom drive, the computer freezes after 15-20 seconds. and when i leave on in when i boot up, it freezes when it gets to the hardware abstraction layer. it works fine in xp. i installed ubuntu 5.10, but upgraded before i used my cd drive, so it probably happend from the upgrade, since i had no trouble installing ubuntu.
oh, and im not sure if it related, but when i tried to install a cdrw drive in xp, it slowed it down considerably, even when i had it plugged in and i reinstalled xp. i figured the drive had problems, and i didn't really need it, as it was from a scrapped computer.
i'd love to use linux more than just to explore, but i can't install games unless i have a cd drive, or i can get my ntfs partition to work (but that's a seperate issue), and it's a hassle to switch back and forth from xp.

---

### Post by Joeb on 2006-06-07
Are you sure that you have your drive jumpered correctly?  If it is on the same cable as your hard drive, the hard drive should be jumpered as the master and the dvd as the slave.  If it is on it's own cable, it should be jumpered as the master.

If you have two drives on the same cable jumpered as master, they will fight each other for control.  Of course, the dvd will only do so when it has a disc in.  Likewise, a single drive jumpered as slave won't function properly.  A dvd in this configuration will only malfunction, again, with a disc.

---

### Post by veloxdraco on 2006-06-07
im almost positive its set to master, but it would be a hassle to check. i have 2 hard drives on one cable (xp and ubuntu) which i know is jumpered correctly, i double checked when i added the second drive, and my dvdrom on the other with a cdrw thats not powered. if i have my dvdrom set to slave, would it still work with windows, or let me install ubuntu? would the second drive, though unpowered, be noticed as master or slave?

i guess ill just take them both out and make sure theyre jumpered right, then maybe i can finally write cds in xp.

thanks

---

### Post by Joeb on 2006-06-07
If your cdrw is set to master but is unpowered, your dvd can still work but would be flaky.  It should work, but slowly, because it would have to time out waiting for the master to fail (but I'm not positive on that).

I would try unplugging the cable from the cdrw, since it's unpowered and see if your problem clears up in both Windows and Ubuntu.

---

### Post by veloxdraco on 2006-06-07
ok, i got the cdrw drive to work, it was set to master, so i switched it to slave and plugged in the power. the dvdrom drive still does the same thing, but the cdrw drive works fine, both in linux and windows. i guess i can live with not having a dvd drive, since the only thing ive ever used them for is linux install disks, and it always works to boot from.

thanks for your help. if anyone else can help me get my dvdrom drive to work, also, it would be great.

---

### Post by Joeb on 2006-06-09
[QUOTE=veloxdraco]ok, i got the cdrw drive to work, it was set to master, so i switched it to slave and plugged in the power. the dvdrom drive still does the same thing, but the cdrw drive works fine, both in linux and windows. i guess i can live with not having a dvd drive, since the only thing ive ever used them for is linux install disks, and it always works to boot from.

thanks for your help. if anyone else can help me get my dvdrom drive to work, also, it would be great.[/QUOTE]

Does the dvd drive work ok in Windows or does it act up both in Windows and Linux?  I'm glad you got the cdrw working!

---

### Post by veloxdraco on 2006-06-09
they both work just fine in windows, even with some virtual drives, too. my only problem now is my dvdrom drive in linux.

---

