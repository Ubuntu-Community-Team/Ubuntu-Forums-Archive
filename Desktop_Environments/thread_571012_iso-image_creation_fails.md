---
title: "iso-image creation fails"
date: 2007-10-08
forum: Desktop Environments
---

### Post by Nick.D on 2007-10-08
I have a data CD, I am trying make a iso-image of that CD as follows.  Right click on the transient desktop icon of that CD -> Copy CD -> Copy disk to -> File image.  A progress bar appears for the next 5 seconds and then goes away as if the program had crashed.  I tried to get GnomeBaker to do the same thing, but it failed with the following error message:

Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Device or resource busy)... giving up.
readom: Device or resource busy. Cannot open '/dev/hda'. Cannot open SCSI driver.
readom: For possible targets try 'wodim -scanbus'. Make sure you are root.
readom: For possible transport specifiers try 'wodim dev=help'. 

Anybody know what the problem is and how to solve it?

---

### Post by Blah3 on 2007-10-08
Did you check the [all-knowing-super-califajilistic-comity-ubuntu-cd-burning-documentation]("https://help.ubuntu.com/community/BurningIsoHowto")?  Otherwise I'll do the confused-programmer-thing i.e. blame the hardware.

---

### Post by Nick.D on 2007-10-08
Blah3,

Thanks.  I just tried this one minutes ago:

dd if=/dev/hda of=$HOME/main/cd.iso bs=64k

and it worked.  So, the hardware seems to be fine.

---

### Post by logos34 on 2007-10-08
You can use the mkiso command

Make a new directory in your home folder and copy all the files on the cd to it.

then create iso:
[B]
mkisofs -J -o filename.iso directoryname[/B]

---

### Post by jjstiff on 2008-02-13
Yeah. I was having the same problem. I put

dd if=/dev/cdrom of=test.iso bs=64k

and it copied fine. no cool gui tho.

Then i moved the image to the Desktop and burned it through nautalis. The copy appears to have worked.

---

