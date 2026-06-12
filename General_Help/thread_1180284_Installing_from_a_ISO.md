---
title: "Installing from a ISO"
date: 2009-06-06
forum: General Help
---

### Post by somerandomzealot on 2009-06-06
First let me say I am really new to Unbuntu, in fact I was a windows user until a year ago.  Now that is out of the way let me get to my problem.

I am currently trying to install Fallout 3 from a ISO.

After having got fed up with the console I moved over to trying to use Gmount

After setting a folder(named ISO)  in my home folder I made it my mount point and then told Gmount to mount the Fallout 3.iso

This is the error message I received:

An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I Don't know what any of that means

also when I tryed to use the base archive manager I was given the error message:
CD-ROM is NOT in ISO 9660 format

I then checked the Fallout 3.iso file type and found this:
raw CD image (application/x-cd-image)

I hope this is enough information for somebody to help me with my problem

I am running jaunty Jackalope 9.10 (I belive) and Wine 1.1.22

Please help

---

### Post by joezamboni on 2009-06-06
mount ./yourmom

---

### Post by somerandomzealot on 2009-06-06
I'm desperately trying to avoid burning it because I'm not sure how to split it between 2 DVD roms...its 5.5g and I only have 4.7 Roms

---

### Post by JCoster on 2009-06-06
It looks like you have a bad ISO.  You should be able to easily extract it.  If not then see if there is a checksum from wherever you got it from and see if they match.

---

### Post by somerandomzealot on 2009-06-06
how do I go about doing that?

---

### Post by Chronon on 2009-06-06
If it has an md5 checksum then you can use the md5sum program.

---

### Post by JCoster on 2009-06-06
Where did you get the ISO from?  Did you make it yourself?  If not then we're verging on breaking forum rules.

---

