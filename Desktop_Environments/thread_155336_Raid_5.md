---
title: "Raid 5?"
date: 2006-04-04
forum: Desktop Environments
---

### Post by countryboy on 2006-04-04
Hello all

Can anyone point me in the right direction to do a RAID 5 (software raid ) of uBuntu?

I'm following the same steps I used succesfully to install a RAID 1 server (from [https://wiki.ubuntu.com/Installation/LVMOnRaid](https://wiki.ubuntu.com/Installation/LVMOnRaid) it bombs out when it tries to install LILO - error code 1

I have 3 160gb SATA disks and have disabled to FakeRAID controller, yet the installation still doesn't work.

Thanks

---

### Post by Alexander Grundner on 2006-04-30
Here's a couple good links for a software RAID setup. I haven't tried them yet, but others in the forum have pointed to these references as well. Good luck!
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

---

### Post by lha on 2006-05-01
You cannot boot from raid5 array with lilo or grub. You have to put /boot (or root) on a raid1 device if you want to raid it. A good solution is to create a small raid1 partition in the beginning of each of your drives and use them to create a raid1 device that is used as /boot, then use the rest of your drives for a raid5 device.

---

### Post by Alexander Grundner on 2006-05-01
Is this necessary even when you configure your software RAID 5 with **mdadm**? (BTW, LinuxDevCenter has a good [howto on mdadm](http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html))

---

### Post by lha on 2006-05-01
[QUOTE=Alexander Grundner]Is this necessary even when you configure your software RAID 5 with **mdadm**? (BTW, LinuxDevCenter has a good [howto on mdadm](http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html))[/QUOTE]
Yes.

---

### Post by countryboy on 2006-05-01
[QUOTE=lha]You cannot boot from raid5 array with lilo or grub. You have to put /boot (or root) on a raid1 device if you want to raid it. A good solution is to create a small raid1 partition in the beginning of each of your drives and use them to create a raid1 device that is used as /boot, then use the rest of your drives for a raid5 device.[/QUOTE]
You're correct, that is exactly the way that I did it. A RAID1 boot partition and a RAID5 data partition. However, when I removed one of the disks (while the server was witched off) it booted up fine, but when I put it back in it failed to boot. I read something somewhere about the order of disks changing or something but could never quite figure it out.

---

### Post by Alexander Grundner on 2006-05-01
That bites. It seems that if you setup your GRUB boot loader to md0 (which is supposed to be your array that shows up as one drive) Ubuntu would boot up normally. If this isn't the case, and RAID1 boot partition didn't work either, then maybe it's best to have Ubuntu installed on a small single drive and have the array work seperately as an additional drive.

Question: When using a software RAID setup to store your files, what happens when your OS gets corrupted or you switch distributions? Do you lose the ability to retrieve your data?

---

### Post by lha on 2006-05-12
[QUOTE=Alexander Grundner]Question: When using a software RAID setup to store your files, what happens when your OS gets corrupted or you switch distributions? Do you lose the ability to retrieve your data?[/QUOTE]

No, you don't. Atleast I can mount my raided partitions from my secondary install. It didn't need any configuration, so I believe there's no magical information stored in the os that originally created raid devices.

---

### Post by Alexander Grundner on 2006-05-12
If that's true, Iha, that's a relief :)

---

