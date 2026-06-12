---
title: "Ubuntu Download Issue"
date: 2006-02-18
forum: Desktop Environments
---

### Post by khalidmian on 2006-02-18
I have tried Various times to download  ubuntu-5.10-install-i386.iso  for installation on my PC. Unfortunately everytime I have been able to download the iso, the iso is corrupted. I have utilized checksum to verify integrity check on iso and the checksum has always failed on ubuntu integrity.
Is there any one who can assist is telling me where i can download and iso that does not have integrity issues?
Thanks

---

### Post by cilynx on 2006-02-18
Well, the official mirror list is at: [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

You can also get a torrent file from any of the mirrors.

If you pull off of one of the official mirrors and still have checksum issues, you're probably actually looking at issues with your current filesystem or some such corrupting your data.

I have a copy that I just verified available if you want:

[http://saint.wolfteck.com/~rcw/](http://saint.wolfteck.com/~rcw/)

---

### Post by khalidmian on 2006-02-20
I downloaded the verified copy...unfortunately without avail...it doesnt work
..it too has errors due to which i had to abort my installation...any help/suggestions?

---

### Post by Digidiz on 2006-02-20
i have downloaded the dvd version, it has worked, i know its whatever gigs, but get bittorent to download it, make sure the upload slider is way down to the 4kb mark. i think those cd versions are really upgrades and not fully functional

---

### Post by cilynx on 2006-02-20
The CD versions are fully functional.  The problem is that cd images are prone to corruption.  I don't know why.  I never had problems with it before a couple weeks ago.  I've even seen tha situation that I checked the md5sum right before doing the burn and it was fine.  When I checked the md5sum of the iso after doing the burn, it was broken.  I was burning using thu built in gnome easy-burning thing.  I wasted maybe 5 cd's burning copies that I had just verified.  All failed.  Eventually, I downloaded a fresh copy, verified the md5 and burned with k3b.  It went flawlessly.  The machine I was burning with had been working perfectly until I upgraded to dapper.  Since then, I have the burning problem in Gnome and the machine hard locks every onw and then for absolutely no good reason.

---

### Post by taurus on 2006-02-20
[QUOTE=cilynx]The machine I was burning with had been working perfectly until I upgraded to dapper.  Since then, I have the burning problem in Gnome and the machine hard locks every onw and then for absolutely no good reason.[/QUOTE]
I guess the magic word here is Dapper!!!  It is a beta so your mileage varies...  If you want to have a stable version, stick with Breezy and wait for Dapper to come out in April.

---

### Post by cilynx on 2006-02-20
Yeah, I know the wonder of Beta versions.  That's why I keep one machine running Debian stable at all times.  But, you know...stable just doesn't have the neat toys.  Back on topic, I just don't grasp why burning a cd (which should be a read only operation on the iso) would mess over the file.

---

