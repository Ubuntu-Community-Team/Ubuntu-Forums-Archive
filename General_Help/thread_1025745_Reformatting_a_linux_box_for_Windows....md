---
title: "Reformatting a linux box for Windows..."
date: 2008-12-30
forum: General Help
---

### Post by inzania on 2008-12-30
I'm in the process of selling my old laptop, which currently has only Ubuntu installed.  I want to put Windows on it to sell it for obvious reasons, but when I boot in the Windows XP Pro CD, the installer insists that it cannot find a hard drive.  Being that Ubuntu works fine, the only thing I can think of is if partitioning the drive for Linux somehow has hidden the drive from Windows.  Does this make sense?  Does anybody have any suggestions?  Thanks!

**EDIT** The problem has been solved; apparently the ThinkPad T60s use SATA hard drives (there was a compatability option in the bios that fixed the problem), so ultimately the problem had nothing to do with Linux or the drive formatting at all.  Woot!

---

### Post by AlanR8 on 2008-12-30
Just had a similar problem on a Dell Dimension desktop and my son's HP Pavilion laptop.

Both machines were more than happy to work under Kubuntu, the Dell was a dual boot and the HP a sole Kubuntu boot.

However, I had to reinstall XP on the Dell and found my original install disk was corrupt. There was NO WAY it would accept another version of XP Pro, and neither would the HP.

I had to pay Dell £20 to get a new installation disk that worked perfectly and I had to turn the house upside down to find the HP installation disks.

All ended well but I did a bit of research on this and there's something called "slip streaming" that maybe you could look at. Did you machine need special drivers for the HD?

---

### Post by ju2wheels on 2008-12-30
Pop in a Ubuntu livecd, install gparted and ntfsprogs. Then run the Partition Editor and format your laptops drive to NTFS and try the Windows CD again.

---

### Post by redilyn on 2008-12-30
To go along with ju2wheels answer. 

I would boot from the livecd and delete all partitions and then try to install Windows.

---

### Post by kokkus on 2008-12-30
This is an old pc right? so have you tried to run winxp on this pc before?
I won't recommand windows on an old PC unless it has more then 1gb ram.
If your old pc runs with 512, 756 mb ram or less, I wouldn't replace it with windows xp.

---

### Post by jimv on 2008-12-30
He's selling it and >=256 mb of RAM is fine for XP.

---

### Post by redilyn on 2008-12-30
> 
He's selling it and >=256 mb of RAM is fine for XP.


If it has 256mb of ram he will be glad he is selling it. 

While it will install and run with 256mb, 512mb is the minimum to get any kind of decent performance out of Windows XP

---

### Post by kokkus on 2008-12-30
I wouldn't even bye a 256mb ram PC, not even if the pc was for free. Trash it my friend.
And no, xp won't work smoothly on that PC. I suggest you just to keep ubuntu installed on it.

---

### Post by redilyn on 2008-12-30
LoL, he never did post any specs. I think this is all speculation :)

Anyways we are way off topic.

---

### Post by blazercist on 2008-12-30
Perhaps the HDD is SATA?  XP has to be hacked to recognize SATA drives, it won't install unless its SP3 or later I believe.

---

### Post by oilchangeguy on 2008-12-30
> **kokkus said:**
> This is an old pc right? so have you tried to run winxp on this pc before?
I won't recommand windows on an old PC unless it has more then 1gb ram.
If your old pc runs with 512, 756 mb ram or less, I wouldn't replace it with windows xp.

you do understand xp is almost 8 years old, right? when it came out most computers had 128mb of ram. xp will run fine on 256. as with most operating systems more ram is better. but in this case, the op is selling the computer.

---

### Post by inzania on 2008-12-30
Thanks all.  It's a ThinkPad T60 with 2 gigs of RAM and a dual-core processor; it's more than adequate for WinXP - I'm a computer programmer and frequently update my system, thus the reason I'm selling a decent machine :)  The Windows CD definitely was not the problem, as I've used the same CD on other machines.  It's also not a SATA drive and does not require any special drivers AFAIK.  I'll try the gparted solution, hopefully getting the drive back to NTFS will solve the problem.

---

