---
title: "verified md5 for ISO?"
date: 2005-11-02
forum: Desktop Environments
---

### Post by geuis on 2005-11-02
I've downloaded the [http://us.releases.ubuntu.com/releases/kubuntu/breezy/kubuntu-5.10-install-i386.iso](http://us.releases.ubuntu.com/releases/kubuntu/breezy/kubuntu-5.10-install-i386.iso) installer 2 times and both of my CDs have been corrupted after burning. (yes, 2nd time I did it at 4x instead of 40x.)

I've read multiple people recommending different md5 verifying programs, which I've duly downloaded.. 

I cannot seem to find a verified checksum value for the actual ISO!

Instead of having to verify checksums for hundreds of files, why can I not just get the md5 of the iso file and compare that to the verified md5 for that ISO?

---

### Post by beefsprocket on 2005-11-02
Check the md5sums file shown here: [http://cdimage.ubuntu.com/kubuntu/releases/breezy/release/]("http://cdimage.ubuntu.com/kubuntu/releases/breezy/release/")
[http://cdimage.ubuntu.com/kubuntu/releases/breezy/release/MD5SUMS]("http://cdimage.ubuntu.com/kubuntu/releases/breezy/release/MD5SUMS")

Oops: those are for the dvd release only. Regular cd-iso's here:
[http://us.releases.ubuntu.com/releases/kubuntu/breezy/](http://us.releases.ubuntu.com/releases/kubuntu/breezy/)

---

### Post by geuis on 2005-11-02
Hey, that did the trick. 

2nd question, can I do a complete install from the kubuntu-5.10-live-i386.iso image?

---

### Post by beefsprocket on 2005-11-02
I believe that this is the page you'd want for a kubuntu livedvd/install dvd:
[http://cdimage.ubuntu.com/kubuntu/releases/breezy/release/](http://cdimage.ubuntu.com/kubuntu/releases/breezy/release/)

For ubuntu, you want oneof these isos:
[http://cdimage.ubuntu.com/releases/breezy/release/](http://cdimage.ubuntu.com/releases/breezy/release/)

I'm not sure that the regular (<700mb iso) livecd includes an install feature, but I'd imagine that it does -- having never used a breezy livecd I can't say either way.

---

