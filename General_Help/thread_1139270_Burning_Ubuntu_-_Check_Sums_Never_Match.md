---
title: "Burning Ubuntu - Check Sums Never Match"
date: 2009-04-26
forum: General Help
---

### Post by Adler on 2009-04-26
Hi All,

I've been running various Linux distributions for years and I'd stopped running .deb versions in favor of .rpm versions.

The reason is that the check sums never match with .deb versus .rpm using K3B. 

I burn always at the lowest possible speed. 

I've just tried to burn Jaunty, but again the check sums don't match. I'll rock along with openSuSE until I get this figured out.

Regards,

JJMacey

---

### Post by sgosnell on 2009-04-27
Well, no, the checksums wouldn't be the same for different files.  A .deb isn't the same as a .rpm.

---

### Post by Adler on 2009-04-27
Duh,

Let me simplify this. When I d/l an Ubuntu version and try to burn it to CD using K3B the check-sum never works when I click to verify data.

I've never had a problem with any .rpm version.

Alles Klar?

Regards,

JJMacey

---

### Post by sgosnell on 2009-04-27
I never had that problem.  But then, I seldom use K3b, preferring brasero.  Maybe it's an openSUSE thing, but I don't recall that problem when I ran openSUSE.  But then again, I never tried to use .deb files with that distro.  Nor do I try to use .rpm files with Ubuntu.

---

### Post by Adler on 2009-04-27
I'll try brasero, but it seems strange that the check sums don't much.

Be right back...

JJMacey

---

### Post by boof1988 on 2009-04-27
> **Adler said:**
> I'll try brasero, but it seems strange that the check sums don't much.

Be right back...

JJMacey

If you want to try *cdrecord* (CLI-style).  It's installed with Ubuntu by default IIRC.  I have had a lot of good luck using it...

```
cdrecord -v dev=/dev/cdrom file-to-burn.iso
```

---

### Post by Adler on 2009-04-27
sgosnell,

I did the burn with Brasero, and it worked. It seems the difference was "check sum" and "fixating". That between K3B and Brasero.

Strange that there is that difference between open source burners.

UBUNTU - I'll be back!

Thanks for that!

JJMacey

---

### Post by yabbadabbadont on 2009-04-27
K3b has had the verify mismatch bug for quite a while now.  I use it, but I just don't have the verify option turned on.  You can manually verify the checksum by running md5sum on the ISO file in a terminal, and then against the CD/DVD device after you have burned your disk.

Example:```
md5sum CD-DVD-Image-File.iso
md5sum /dev/hdc
```
Change /dev/hdc to the correct device on your system.

These two commands will spit out a checksum.  If they match, everything went fine with the burn.

---

### Post by Adler on 2009-04-27
yabbadabbadont,

Consider me "old school". I like to see it done right.

Normally I do run "verify data" with K3B, it has served me well burning all kind of things.

Thanks for the reply.

Regards,

JJMacey

---

### Post by Scotty Bones on 2009-04-27
it seems to be something strange with jaunty (maybe its just me?).  Ever since the nautilus burn extension was replaced by brasero's, I've never had a checksum match.  But, the resulting disks work just fine.

---

### Post by Adler on 2009-05-01
Hi All,

Just another follow-up. I burned both the 32 + 64-bit DVDs with K3B and the check sums matched. They didn't with the CDs even at the slowest speeds available. Go figure...

I do like the new Ubuntu 9.04. I was too lazy to fight with the 64-bit version e.g. apps, so did the 32-bit install.

I do like the new Ubuntu, and have just dropped openSuSE11.1.

Regards,

JJMacey

---

