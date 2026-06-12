---
title: "Ubuntu 10.10 installation problem"
date: 2010-12-30
forum: Desktop Environments
---

### Post by choi36 on 2010-12-30
Hey. Ok so I'm new with ubuntu trying to install the ubuntu 10.10 64bit iso that I downloaded from ubuntu's site.  Burned at a slow speed and tried the install. First i did the install on a clean drive only to have the install hang right after the splash screen wtih the logo and the five dots, the splash disappears but nothing comes up except for a cursor.  
Second I tried to install from windows, which completes. But when i reboot to verify/finish I get an I/O error. So I download another copy of the iso burned that and tried again with the same result.
Any ideas??

---

### Post by karthick87 on 2010-12-30
Welcome to ubuntuforums :)

Verify your hash codes in the following link,

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by judedawson on 2010-12-30
Hi choi36,

Just checking here... after downloading the iso file, did you verify the md5 sum or sha256 sum (hash) of the .iso file ?

You can get more information here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM)

It would be good to check your iso files before burning them to disk / making a bootable thumbdrive. You may need to download the iso file again, perhaps.

Most of the installation problems of iso files which I have encountered were due to damaged iso files during download.

The md5 sum or sha256 sum checks saved me a lot of time I would have otherwise spent troubleshooting.

Hopefully, this helps you.

From,
Jude

---

### Post by choi36 on 2010-12-30
Yeah I checked the md5sum and it is legit

---

### Post by judedawson on 2010-12-30
What are the specs of the machine you are installing Ubuntu 64-bit on?

---

### Post by choi36 on 2010-12-30
AMD Athlon 4400 Dual Core, 2GB RAM not sure what else you want to know

---

### Post by Whyzer on 2010-12-30
When you say it hangs after logo screen had you had a chance to specify the install instructions yet? Try this.. When you get to 1st screen you'll see along the bottom some F1, F2 instructions. Just hit F6 which will pull up a mini menu with several items, at the bottom is nomodeset, select it and hit ESCAPE. Once it clears the menu you'll see a line at the bottom of the screen and it ends in "quiet splash --"  use the backspace key to erase just the quiet spash and anything after it and type in nomodeset 
then hit enter to install Ubuntu and it should work. This is happening probably because you have an NVidia graphics card so some other odd type. There are no NVidia drivers for 10.10 yet (which is why I am using 10.04, I still had to do the nomodeset, but after I did my first update Ubuntu had the drivers for it).
When you reboot this could happen again, if it does you're going to have to enter Grub by hitting X, once in hit E to edit and get rid of the quiet splash again and replace it with nomodeset.
If you do have an NVidia card, your going to need to permantly fix this (since editing it at boot is a temporary thing).  

 To do this you're going to have to do to a terminal screen (looks like a DOS window) and type sudo gedit /etc/default/grub this will bring up a text editor which once and for all fix the quiet splash / nomodeset issue for good or until NVidia writes drivers for 10.10
Hope this helps

---

### Post by choi36 on 2010-12-30
Ok so the disc works now don't ask how it just does and I'm willing to accept that. However, now during the install I get an error when its trying to create the file system while "The ext4 file system creation in partition #1 of SCSI1(0,0,0) (sda) failed". When given the option to how to partition/use the drive I just choose to sue the whole thing. Should I choose the last option and allocate the space myself? 

Oh and no I don't a nVidia video card, I have an ati. My mobo does have an nVidia chipset

---

### Post by foxmulder881 on 2010-12-30
Sounds like a hard disk issue if you ask me.

I'd completely wipe the drive using something like UBCD and then verify the drive surface to ensure there's no bad sectors.

---

### Post by choi36 on 2010-12-30
I was thinking maybe the same thing, I was just gonna get a new drive and see what happens.

---

