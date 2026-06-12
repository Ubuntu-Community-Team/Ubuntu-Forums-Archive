---
title: "(Crosspost) Updating your Dell's System BIOS from Ubuntu"
date: 2007-06-10
forum: Dell  Ubuntu Support
---

### Post by neptho on 2007-06-10
This HOWTO is now out of date.

Please see [here](http://linux.dell.com/wiki/index.php/Tech/libsmbios) on Dell's Wiki for easier (compatible) instructions, now that these tools are available natively within Ubuntu.

The old FAQ is below:



**First, the Linux direct method: (Scroll down to see how to use a method with a FreeDOS boot system):**

Note that when I prepend a line with a '%', that means you open a terminal and do it at the prompt; yours may look different.  That's fine.  Everything should just work.  *This MAY NOT WORK IF YOU KILLED YOUR DELL BIOS SUPPORT PARTITION; YOU HAVE BEEN WARNED!*  :)

First of all, you'll need to install the smbios support libraries; these are available within the Ubuntu repositories:

```
%sudo apt-get install libsmbiosxml1 libsmbios-bin libsmbios1
```

Next, you're going to need the firmware-tools and firmware-addon-dell packages.  I've built my own from [Dell's etch build sources](http://linux.dell.com/repo/software/debian/dists/etch-i386/).  These are for IA32, if you need x64, that's a directory up, and sorry, I can't offer those, I do not have an x64 installation to test with.

You may use my i386 builds if you wish, I've signed my debs, you can check them with dpkg-sig:
```
%wget http://www.holwegner.com/files/firmware-addon-dell_1.2.13-1_i386.deb
%wget http://www.holwegner.com/files/firmware-tools_1.2.6-1_all.deb
```

You can get my key and add it to your keyring:
```
%gpg --keyserver wwwkeys.eu.pgp.net --recv-keys F8C314E3
gpg: requesting key F8C314E3 from hkp server wwwkeys.eu.pgp.net
gpg: key F8C314E3: public key "Shawn Holwegner (GPG Signing Key) <shawn@holwegner.com>" imported
%gpg --armor --export F8C314E3 | sudo apt-key add -
OK
```

Now, you can check my signature; I've tagged both as 'feisty' (Note that I have left the response of GPG here so you can ensure they match):
```
%dpkg-sig -c firmware-addon-dell_1.2.13-1_i386.deb
Processing firmware-addon-dell_1.2.13-1_i386.deb...
GOODSIG _gpgfeisty 743D4D271144FB13C788D9F3B4B33515F8C314E3 1181453286
%dpkg-sig -c firmware-tools_1.2.6-1_all.deb
Processing firmware-tools_1.2.6-1_all.deb...
GOODSIG _gpgfeisty 743D4D271144FB13C788D9F3B4B33515F8C314E3 1181453298
```

Now, if you trust me, install them:
```
%sudo dpkg -i firmware-tools_1.2.6-1_all.deb firmware-addon-dell_1.2.13-1_i386.deb
```

Find out your system ID.  Note that this is the area in bold:

```
%sudo getSystemId
Libsmbios:    0.12.1
System ID:   **0x01BD**
Service Tag:  6H5GMB1
Express Service Code: 14097792493
Product Name: MM061
BIOS Version: A11
Vendor:       Dell Inc.
Is Dell:      1
```

Go to [http://linux.dell.com/repo/software/bios-hdrs/](http://linux.dell.com/repo/software/bios-hdrs/) and find your system, the directory will be **system_bios_ven_0x1028_dev_SYSTEM_ID_version_THE_BIOS_VERSION**, in the case of my Inspiron 6400, mine was: **system_bios_ven_0x1028_dev_0x01bd_version_a15** for my System ID of **0x01BD** and BIOS version **A15**.

Download the "bios.hdr" file from that directory.
```
%wget http://where/your/bios/is/bios.hdr
```

Load the "dell_rbu" support module into the kernel:
```
%sudo modprobe dell_rbu
```

Finally, flash the BIOS:
```
%sudo dellBiosUpdate -u -f ./bios.hdr
Supported RBU type for this system: (MONOLITHIC)
Using RBU v2 driver. Initializing Driver. 
Setting RBU type in v2 driver to: MONOLITHIC
Prep driver for data load.
Writing RBU data (4096bytes/dot): ............................
..............................................................
.......................
Notify driver data is finished.
Activate CMOS bit to notify BIOS that update is ready on next boot.
Update staged sucessfully. BIOS update will occur on next reboot.
```

Now, when you reboot, the system will flash to the BIOS you've downloaded, and reboot.  Enjoy your new BIOS, I'm enjoying the microcode updates in A15 as I type this!  ;)

**FreeDOS boot image method (I have not attempted this, personally):**
> **gray wolf said:**
> The method that I've used twice so far is documented on Dell's website at [http://linux.dell.com/projects.shtml#biosdisk](http://linux.dell.com/projects.shtml#biosdisk).

---

### Post by Pcniatic on 2007-06-14
Thank you, it did work for me upgrading my dell 640m/E1405 from bios version A09 to A10.
It was and urgent upgrade and it worked without a problem.
Thanks for the packages.

---

### Post by neptho on 2007-06-15
Duplicate

---

### Post by The Groovy Guru on 2007-06-15
Does anyone have any ideas about what to do if you've killed your BIOS partition? Is it possible to replace it?

---

### Post by bapoumba on 2007-06-17
@  neptho: I've merged the two threads.

---

### Post by neptho on 2007-06-17
> **The Groovy Guru said:**
> Does anyone have any ideas about what to do if you've killed your BIOS partition? Is it possible to replace it?

Unless you're very adept at repartitioning and reinstalling tools, you need to reinitialize your hard disk.  Dell's solution is to wipe and reinstall from scratch.

However, if you make a small bootable DOS (FAT16) partition, and copy over ALL of the support tools, then use fdisk to change the type to 0xDE (fdisk /dev/sda or /dev/hda; t (partition #), de, w, q), it should be fine.

Just make sure you 'SYS' the drive so it's bootable.  This is best done with a bootable dos diskette made to an ISO bootable image.  ;)

> **bapoumba said:**
> @  neptho: I've merged the two threads.

That works.  Removed my second entry since it's 100% duplicated info.  :)

---

### Post by The Groovy Guru on 2007-06-18
Thanks neptho, that sounds doable.

One more question - I notice on the Dell site they have a dos program to update your bios. Is it ok to just make a bootable Dos CD and run it without doing anything else or is that not a good idea?

---

### Post by neptho on 2007-06-19
> **The Groovy Guru said:**
> One more question - I notice on the Dell site they have a dos program to update your bios. Is it ok to just make a bootable Dos CD and run it without doing anything else or is that not a good idea?

Due to the differences in various systems, I wouldn't trust it without having a full DOS 6.2 system with the ability to enable/disable HIMEM.

The biggest problem you can run into is that some of these programs want to write a backup, just in case if they get a CRC error.  If it sees your virtual floppy as read-only, I have no idea how delicately the program can handle that.

---

### Post by The Groovy Guru on 2007-06-19
Thank for the help Neptho :)

---

### Post by dutch1918 on 2007-06-19
I'm wondering wether it is worth upgrading the BIOS when it's not broke yet :)

I have the the following:

Product Name: MM061
BIOS Version: A12

---

### Post by neptho on 2007-06-19
I have the same machine.  I upgraded to A15, because I was A14, and I started having overheating problems.

Unless you have one of the newest CPUs, it probably won't affect you drastically, but I know A14 does have CPU microcode updates; and A14 had killed my automatic fans (turned the threshhold really high).

---

### Post by Pe2 on 2007-06-28
Hi

Thanks for a nice guide!
When i choose a bios to download, do I then choose the one I want or the one I have?

Printout of getSystemId:
```

Libsmbios:    0.13.6
System ID:    0x0149
Service Tag:  8Q30X0J
Express Service Code: 18991460899
Product Name: Inspiron 1100
BIOS Version: A22
Vendor:       Dell Computer Corporation
Is Dell:      1

```

If i'm to select the one i've got then I can't seem to find it. The list starts with 0x0149 _a23.

Edit:
I've tried several other versions of the 0x0149 bios, but everytime I get the same error saying I don't have the correct ROM.

Any ideas?

---

### Post by neptho on 2007-06-28
> **Pe2 said:**
> Hi

Thanks for a nice guide!
When i choose a bios to download, do I then choose the one I want or the one I have?

Printout of getSystemId:
```

Libsmbios:    0.13.6
System ID:    0x0149
Service Tag:  8Q30X0J
Express Service Code: 18991460899
Product Name: Inspiron 1100
BIOS Version: A22
Vendor:       Dell Computer Corporation
Is Dell:      1

```

If i'm to select the one i've got then I can't seem to find it. The list starts with 0x0149 _a23.

Edit:
I've tried several other versions of the 0x0149 bios, but everytime I get the same error saying I don't have the correct ROM.

Any ideas?

0x0149 is correct, and the A23 is the next upgrade.  It should flash. What specific error are you getting?

Since you are a Breezy user (or haven't updated your profile), there are likely changes in the kernel module which may not be supported by these tools; you may try building your own version.

---

### Post by Pe2 on 2007-06-30
I haven't updated my profile, i'm running gusty at the moment. 

The error says it can't find the required ROM for the operation.

---

### Post by neptho on 2007-06-30
> **Pe2 said:**
> I haven't updated my profile, i'm running gusty at the moment. 

The error says it can't find the required ROM for the operation.

This is incredibly strange; can you try again and cut and paste the error message?  I'll see if I can find something in the code, but I'm stumped as to why it would be complaining with the proper System ID (and being that I don't work for Dell, I probably won't get too much farther..)

---

### Post by Pe2 on 2007-07-01
I can't copy past the erros since it happens when the update was supposed to happen. 
But here is a rough transcript of it:

Updating bios: ....
[3 sec...]
ERROR! The update could not be performed because a valid ROM file could noe be found.
Press 'Y' to continue

---

### Post by neptho on 2007-07-01
So, you're getting this message at the 'grey screen' BIOS update where it says 'Dell BIOS update', and not within Linux?  If that's the case, it may be getting munched when in transfer, but the dell_rbu module tests for that, so I'm at a loss.  Did you kill your Diagnostic partition?

---

### Post by khedron on 2007-07-01
Sorry for being a bit off-topic here, but will this howto work with a Dell that I have manually installed Linux onto? (I.e. one which Dell does not support putting Linux on.) I currently have to boot into Windows to perform a BIOS upgrade, and would like to do it in Ubuntu.

---

### Post by neptho on 2007-07-01
> **khedron said:**
> Sorry for being a bit off-topic here, but will this howto work with a Dell that I have manually installed Linux onto? (I.e. one which Dell does not support putting Linux on.) I currently have to boot into Windows to perform a BIOS upgrade, and would like to do it in Ubuntu.

Yes, it will, you just have to install the tools I've precompiled for use with Feisty; or build them, yourself - They're not included with the base Ubuntu installation.

---

### Post by gray wolf on 2007-07-02
The method that I've used twice so far is documented on Dell's website at [http://linux.dell.com/projects.shtml#biosdisk](http://linux.dell.com/projects.shtml#biosdisk).

You basically create a bootable disk image and boot from that. I works very nicely.

---

### Post by neptho on 2007-07-02
> **gray wolf said:**
> The method that I've used twice so far is documented on Dell's website at [http://linux.dell.com/projects.shtml#biosdisk](http://linux.dell.com/projects.shtml#biosdisk).

That's pretty slick, thanks for adding this information.  I'll add it to my intial post.

---

### Post by Pe2 on 2007-07-02
> **neptho said:**
> So, you're getting this message at the 'grey screen' BIOS update where it says 'Dell BIOS update', and not within Linux?  If that's the case, it may be getting munched when in transfer, but the dell_rbu module tests for that, so I'm at a loss.  Did you kill your Diagnostic partition?

Hmm, I've probably killed it. Just installed Ubuntu with a complete formate of the HD.

I'll just try the new mthod recomended by Grey Wolf.

---

### Post by raggari on 2007-08-17
Do you now if Dell is going to add official ubuntu repos in near future? I'm not going to update my bios with unofficial tools from Dell.

---

### Post by kallistra on 2007-08-20
I have an E1705 and flashed my BIOS from A06 to A09 a couple of days ago following the instructions on the Dell Linux Wiki: [http://linux.dell.com/wiki/index.php/Tech/libsmbios](http://linux.dell.com/wiki/index.php/Tech/libsmbios)
 
It worked for me very well, and the process was smooth. I did sweat a little at first since it was my first time doing a BIOS update in Linux but since I hosed my Windows BIOS Flash, I was what the heck. (Windows crashed in the middle and never would let me flash again, Dell's solution was to redo my install - no freaking way....)
 
Hope that helps.

---

### Post by raggari on 2007-08-23
> **kallistra said:**
> I have an E1705 and flashed my BIOS from A06 to A09 a couple of days ago following the instructions on the Dell Linux Wiki: [http://linux.dell.com/wiki/index.php/Tech/libsmbios](http://linux.dell.com/wiki/index.php/Tech/libsmbios)
 
It worked for me very well, and the process was smooth. I did sweat a little at first since it was my first time doing a BIOS update in Linux but since I hosed my Windows BIOS Flash, I was what the heck. (Windows crashed in the middle and never would let me flash again, Dell's solution was to redo my install - no freaking way....)
 
Hope that helps.

Thanks! I didn't realize that libsmbis includes all necessary binaries for BIOS update. Worked great with  Optiplex 745.

---

### Post by rozen on 2007-09-06
Hi,

I just came across this thread.  I am very reluctant to update the bios.  I am worried that if I do something that trashes the Bios, I won't be able to get my machine to run at all.   So my question is "How does one recover from non working bios?".   I know of no way to reinstall bios on a machine without a working bios.  It seems likely to require that some chip which stores the bios might have to be replaced.  Is it Russian roulette with my hardware?

Am I missing something that should be obvious? 

Thanks in Advance,
Don

---

### Post by neptho on 2007-09-06
> **rozen said:**
> Hi,

I just came across this thread.  I am very reluctant to update the bios.  I am worried that if I do something that trashes the Bios, I won't be able to get my machine to run at all.   So my question is "How does one recover from non working bios?".   I know of no way to reinstall bios on a machine without a working bios.  It seems likely to require that some chip which stores the bios might have to be replaced.  Is it Russian roulette with my hardware?

Am I missing something that should be obvious? 

Thanks in Advance,
Don

To be blunt: You may not.  

With Asus based systems, you can put a boot floppy image in, and it will read the BIOS from the image.  I do not believe  consumer Dell systems offer such a function:  If you break it, you get to keep both pieces.  However, the software does test to ensure things are working, and it should put the old blocks back into place if there is a problem.

Unless you're having a problem, or there's a necessary microcode update, you're fairly safe to not update.  I had to update because my fan was not working with A12.  It started working (without i8kmon) with A14.

Update: A17 is out for my system, and it loaded, but refused to flash to it; the pre-boot BIOS flash screen told me the image was corrupt; I had to press 'Y' to bypass the flash.  The screen went white, then loaded back into A15 BIOS.  I downloaded it again, and this time, the flash worked fine.

---

### Post by sr20ve on 2007-09-06
I never knew there was so much involved in updating the bios. Right after I wiped windows and installed ubuntu on my E1505, I noticed there was a bios update, I wished I would have just updated before wiping windows.

Anyways, I just downloaded the DOS executable bios update, put that on a bootable ISO. Booted off the CD, ran the update, everything went smoothly. Took about 10 minutes, including burning the CD.

---

### Post by neptho on 2007-09-06
> **sr20ve said:**
> I never knew there was so much involved in updating the bios. Right after I wiped windows and installed ubuntu on my E1505, I noticed there was a bios update, I wished I would have just updated before wiping windows.

In truth, after you install the tools, and learn what your system ID is, it's as simple as downloading the new firmware for your machine, loading the flash module, telling it to flash, then rebooting.

---

### Post by jcottier on 2007-09-13
Looks easy, but I cant find a bios file that matches my system ID (0x01EC) . Looking in [http://linux.dell.com/repo/software/bios-hdrs/](http://linux.dell.com/repo/software/bios-hdrs/) the list stops one short at 0x01EB. Does this mean Dell does not support updating all its machines via Ubuntu? I did ask them, but got no sensible response.

---

### Post by magicfab on 2007-09-13
It's interesting in two different systems I tested I could not use the tools described in Dell's howto. I had to use another tool they built 4 years ago which works quite reliably, biosdisk.

See:
[http://ubuntuforums.org/showthread.php?t=549385](http://ubuntuforums.org/showthread.php?t=549385)

What I find particularly cumbersome from the other method is trying to find the appropriate header file. I wouldn't ask anyone over the phone to do that ;)

When I get some more time I'll try again and see what may have gone wrong.

---

### Post by digisus on 2008-01-03
Hello

**EDIT:** Silly me. I forgot to "sudo" the command! It works fine.

I am planning to upgrade the BIOS of my Diemension C521 desktop. But the first step is already a show-stopper:

```
m@ubuntux:~$ getSystemId
Libsmbios:    0.13.6
Error getting the System ID   : Could not instantiate SMBIOS table.
Error getting the Service Tag : Could not instantiate SMBIOS table.
Error getting the Product Name: Could not instantiate SMBIOS table.
Error getting the BIOS Version: Could not instantiate SMBIOS table.
Error getting the Vendor      : Could not instantiate SMBIOS table.
Is Dell:      0
```

Any ideas what the problem may be?

I will just reboot and collect all that information from the BIOS itself. But still, I am a bit worried that this information is not available. Should I defer the BIOS upgrade because of that?

Thanks, 
digisus

---

### Post by manicnerd on 2008-01-04
I dont know what i'm doing wrong but I cant seem to find the header file for my system.....the getSystemId output is:

```

root@rewind:~# getSystemId
Libsmbios:    0.13.6
System ID:    0x022A
Service Tag:  F$$$$$$
Express Service Code: 32903123456
Product Name: Vostro   1000
BIOS Version: 2.6.1
Vendor:       Dell Inc.
Is Dell:      1
```

the files listed dont include an A

```

system_bios_ven_0x1028_dev_0x0215_version_a01/
system_bios_ven_0x1028_dev_0x0220_version_a00/
system_bios_ven_0x1028_dev_0x0227_version_a00/
system_bios_ven_0x1028_dev_0x0227_version_a03/
system_bios_ven_0x1028_dev_0x0228_version_a00/
system_bios_ven_0x1028_dev_0x0228_version_a01/
system_bios_ven_0x1028_dev_0x0229_version_a00/
system_bios_ven_0x1028_dev_0x023c_version_1.0.0/
```

what should I do?

---

### Post by neptho on 2008-01-04
> **manicnerd said:**
> I dont know what i'm doing wrong but I cant seem to find the header file for my system.....the getSystemId output is:

```

root@rewind:~# getSystemId
Libsmbios:    0.13.6
System ID:    0x022A
Service Tag:  F$$$$$$
Express Service Code: 32903123456
Product Name: Vostro   1000
BIOS Version: 2.6.1
Vendor:       Dell Inc.
Is Dell:      1
```

what should I do?

I would not trust that.  Your Service Tag information has to be corrupt, unless you edited it, yourself.

The Vostro 1000 is a very new line, and I believe it uses an entirely different BIOS; It is not the 'standard' Dell BIOS - although this may only be for the AMD revisions of the 1000.

---

### Post by manicnerd on 2008-01-04
thanks for the reply (yes i edited my service tag since you can log in to dells site with it)

---

### Post by omshanti on 2008-07-21
Tried this, and I can't find my system ID in the list -- it's 0x01EC, and the list skips right from EB to EF. Any ideas?

Thanks!

---

### Post by digisus on 2008-07-21
No, no ideas. I have the same problem (just did not bother to finish my last posting months ago).

It seems that all 521 users without Windows are not able to upgrade the BIOS. ](*,)

---

### Post by omshanti on 2008-07-21
Well, that's frustrating. At least I'm not alone -- I'll let you know if I figure anything out. Thanks!

---

