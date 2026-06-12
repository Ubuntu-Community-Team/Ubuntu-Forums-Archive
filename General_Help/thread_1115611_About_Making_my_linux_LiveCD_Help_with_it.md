---
title: "About Making my linux LiveCD? Help with it?"
date: 2009-04-04
forum: General Help
---

### Post by Zedday on 2009-04-04
i've downloaded the ubuntu .iso, now i'm ready to burn it to a CD-RW, what do i [COLOR="DarkOrange"]choose[/COLOR]?...

[COLOR="Red"]1)[/COLOR]**DATA DISC **- allows you to create ISO images, burn usual data discs, MP3-CD's and Video Discs.
[COLOR="Red"]2)[/COLOR]**BURN ISO IMAGE** - allows you to burn ISO images to a disc. 

thank you.

---

### Post by joshrobinson on 2009-04-04
Option 2
Burn ISO image

---

### Post by Zedday on 2009-04-04
> **joshrobinson said:**
> Option 2
Burn ISO image

thank you very much, i was a little confused at first becuase they both talk about ISO Images

im new  =) thanks again

---

### Post by pgmer6809 on 2009-05-19
> **Zedday said:**
> thank you very much, i was a little confused at first becuase they both talk about ISO Images im new  =) thanks again

Are all ISO images bootable?
I have a live CD of gparted_03. It is an ISO image (mount cmd shows it mounted as filetype ISO9660)
If I try to copy it with brasero, brasero wont recognize the blank media in my drive.
So I copied the contents to my home directory and then using right-clik copied the results to CD.
Files end up there OK, but the result is not bootable.

I also tried making an ISO image first using genisofs and then using right clik to burn the cd.
Again the CD is OK, it can be mounted and the files are there, but it wont boot. 
The iso image can also be mounted with the -o loop option and it looks OK.

finally I tried wodim but wodim -scanbus and wodim --devices just give me errors that it cannot find the SCSI driver.

FYI the original CD looks like:

/boot         (has various files in this directory)
/selinux      (has various files in this directory)
gparted_03.dat (one big 44MB file)

and it boots fine on several different computers.

Any suggestions?
Thanks, 
pgmer6809

---

### Post by SentientFluid on 2009-05-19
> **Zedday said:**
> thank you very much, i was a little confused at first becuase they both talk about ISO Images

The first will allow you to *create* an .iso file (or burn the data to a disc).  An .iso is an exact image of what would be burned to a disc.

The 2nd option allows you to burn an already created .iso to a disc so you can use it normally.

> **pgmer6809 said:**
> Are all ISO images bootable?

No, it has to have the proper info written to the boot sector of the disc.

> **pgmer6809 said:**
> I have a live CD of gparted_03. It is an ISO image (mount cmd shows it mounted as filetype ISO9660)
If I try to copy it with brasero, brasero wont recognize the blank media in my drive.
So I copied the contents to my home directory and then using right-clik copied the results to CD.
Files end up there OK, but the result is not bootable.

I also tried making an ISO image first using genisofs and then using right clik to burn the cd.
Again the CD is OK, it can be mounted and the files are there, but it wont boot. 
The iso image can also be mounted with the -o loop option and it looks OK.

finally I tried wodim but wodim -scanbus and wodim --devices just give me errors that it cannot find the SCSI driver.

FYI the original CD looks like:

/boot         (has various files in this directory)
/selinux      (has various files in this directory)
gparted_03.dat (one big 44MB file)

and it boots fine on several different computers.

Any suggestions?
Thanks, 
pgmer6809

Try burning the cd [with these instructions]("https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu") and if it doesn't boot then read these [Common Problems when Booting from CD/DVD]("https://help.ubuntu.com/community/BootFromCD").

And did you verify the checksum of the iso you downloaded?

---

### Post by pgmer6809 on 2009-05-20
> **SentientFluid said:**
> The first will allow you to *create* an .iso file (or burn the data to a disc).  An .iso is an exact image of what would be burned to a disc.

The 2nd option allows you to burn an already created .iso to a disc so you can use it normally.



No, it has to have the proper info written to the boot sector of the disc.



Try burning the cd [with these instructions]("https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu") and if it doesn't boot then read these [Common Problems when Booting from CD/DVD]("https://help.ubuntu.com/community/BootFromCD").

And did you verify the checksum of the iso you downloaded?

I did not download an iso. I have a CD already that boots. I want to copy it.

I tried to copy using brasero but brasero imports the files from the CD but then complains when I insert my blank media and refuses to go further.

I copied the files from the CD to a subDir in my home directory.
Then I used genisofs to make an iso image out of the subdir.
I verified that the iso image is OK by mounting it with the loop option and checking the contents.

I then right clicked on the iso image and burned it to the cd.
I verified that the Cd was burned correctly by mounting it, and verifying that it had the directories and subdirectories on it, and not just one iso file.

I then inserted this CD in another computer and it will not boot.
But when I insert the original CD I am trying to copy into the other computer it boots fine.

So none of the suggestions on the links about burning ISO's relates to my problem. 
1. The ISO is burned correctly.
2. The target computer can boot from CD's. 

When you burn a CD by right cliking do you have to finalize it or anything to make it bootable?

pgmer6809

---

### Post by SentientFluid on 2009-05-21
> **pgmer6809 said:**
> I did not download an iso. I have a CD already that boots. I want to copy it.

Sorry, I misunderstood what you meant by "*I have a live CD of gparted_03. It is an ISO image*".

> **pgmer6809 said:**
> I copied the files from the CD to a subDir in my home directory.
Then I used genisofs to make an iso image out of the subdir.
I verified that the iso image is OK by mounting it with the loop option and checking the contents.

I then right clicked on the iso image and burned it to the cd.
I verified that the Cd was burned correctly by mounting it, and verifying that it had the directories and subdirectories on it, and not just one iso file.

I then inserted this CD in another computer and it will not boot.


The information that your computer needs in order to boot is kept in the *boot sector* of the disc.  The boot sector can't be read by your typical file manager so it can not be copied by dragging and dropping files the way you described.  It's the boot secto that determines whether a disk is bootable or not.

> **pgmer6809 said:**
> But when I insert the original CD I am trying to copy into the other computer it boots fine.

So none of the suggestions on the links about burning ISO's relates to my problem. 
1. The ISO is burned correctly.
2. The target computer can boot from CD's. 

When you burn a CD by right cliking do you have to finalize it or anything to make it bootable?

Technically the ISO is burned correctly but the boot sector wasn't copied/burned to the new disk.  The disk won't boot any computer if the disk doesn't have a boot sector.

I believe the "Copy Data CD" option in Gnomebaker will copy the boot sector *and* the data over to the new disk.  You should be able to install it from the repositories.  I *think* k3b does as well.

Alternatively, download a Gparted LiveCD iso and burn that. It will already have the boot sector info included in the iso so the disk should boot once you're done burning the iso.

---

### Post by pgmer6809 on 2009-05-23
> I believe the "Copy Data CD" option in Gnomebaker will copy the boot sector and the data over to the new disk. You should be able to install it from the repositories. I *think* k3b does as well.

Alternatively, download a Gparted LiveCD iso and burn that. It will already have the boot sector info included in the iso so the disk should boot once you're done burning the iso.



Thanks.
I will try the download ISO approach.
installing gnomebaker wants to de-install cdda2wav, and I have other pkgs which rely on cdda2wav so I don't want to do that.



pgmer6809

---

