---
title: "installation problem"
date: 2005-11-16
forum: Desktop Environments
---

### Post by erakepio on 2005-11-16
I downloaded the Ubuntu install from the website and burnt it to a disk.  This was recognised as a .iso file, which i had no problems with.  I changed my BIOS to boot off CD which worked out, sorted out my partitions (im trying to implement dual boot) and the proceeded with the install.

at about 6% i got an error message saying it could not locate "boostrap.log" so i cancelled the information and using the console tried  searching for the file but it couldnt find it anywhere.  I then downloaded the livecd iso file and when i looked for bootsrap.log i still couldnt find it.

been trying for about two days now to get Ubuntu going on my machine..with the same error and about 3 different copies of both live CD and the install CD iso files.  and im unsure how to alter the speed of that my CD drive burns at

please help!

thank you

---

### Post by andrewsawyer on 2005-11-16
hiya,

Try reburning the iso, only do it a 1x write speed.  Yes - I know it will take a while, but that should fix your problem.

Let us know if you have any more problems.

Andy

---

### Post by mustang on 2005-11-16
Yeah, burn the iso again and to be safe, burn it at a lower speed as the post above suggested.

Afterwards, once you've booted off the cd, look for the option to check the integrity of the disc. That'll check if your cd is okay before you start to install.

---

### Post by gabbman on 2005-11-16
[QUOTE=erakepio]I downloaded the Ubuntu install from the website and burnt it to a disk.  This was recognised as a .iso file, which i had no problems with.  I changed my BIOS to boot off CD which worked out, sorted out my partitions (im trying to implement dual boot) and the proceeded with the install.

at about 6% i got an error message saying it could not locate "boostrap.log" so i cancelled the information and using the console tried  searching for the file but it couldnt find it anywhere.  I then downloaded the livecd iso file and when i looked for bootsrap.log i still couldnt find it.

been trying for about two days now to get Ubuntu going on my machine..with the same error and about 3 different copies of both live CD and the install CD iso files.  and im unsure how to alter the speed of that my CD drive burns at

please help!

thank you[/QUOTE]
I am getting the same error at the same point in the install, and that's using the 'Shipit' cd's.  It does it on any of the 5 I recieved.

---

### Post by andlinux21 on 2005-11-16
can you replace the cd/dvd rom with another one just till you get the install done?:confused:

---

### Post by gabbman on 2005-11-16
[QUOTE=andlinux21]can you replace the cd/dvd rom with another one just till you get the install done?:confused:[/QUOTE]
All 5 of the cd's from Ubuntu, do the same thing at the same point in the install.
The ISO I downloaded and burned of 5.10 is installing just fine though.

---

### Post by erakepio on 2005-11-17
thanks for the response, i appreciate it.  I'm rather new to linux and Ubuntu was recommended to me by a friend so im looking forward to getting it set up and being able to have a play around with it.

i've come across another installation problem..this time it involves the partitioner.  Ubuntu is going to be installed on what was previously my Fdrive..but since converted it to allow an ubuntu installatio (sda10).  yetwheni attempt to run the installation it says there is no boot (or root i cant remember) file system selected, yet when selecting the drive and viewing options..i have the Reiser file system selected yet the installer still seems to think its not selected.  ive tried writing to the disks but the same error occurs.

would formatting that partition perhaps solve the problem??

---

### Post by az on 2005-11-17
[QUOTE=erakepio]thanks for the response, i appreciate it.  I'm rather new to linux and Ubuntu was recommended to me by a friend so im looking forward to getting it set up and being able to have a play around with it.

i've come across another installation problem..this time it involves the partitioner.  Ubuntu is going to be installed on what was previously my Fdrive..but since converted it to allow an ubuntu installatio (sda10).  yetwheni attempt to run the installation it says there is no boot (or root i cant remember) file system selected, yet when selecting the drive and viewing options..i have the Reiser file system selected yet the installer still seems to think its not selected.  ive tried writing to the disks but the same error occurs.

would formatting that partition perhaps solve the problem??[/QUOTE]


Just to answer your first question, the log file youwere looking for was on your ramdisk.  That is why you could not find it afterwards.

When you manually edit the partition table, you have to not only tell it to use a particular partition and filesystsem, but specify it to be your root partition (root is symbolised by "/")

Also, why are you using reiserfs?   Unless you will be running a server with (litterally) a miliion small files to sort, you will not see any benefit.

---

### Post by gabbman on 2005-11-17
[QUOTE=azz]Just to answer your first question, the log file youwere looking for was on your ramdisk.  That is why you could not find it afterwards.

When you manually edit the partition table, you have to not only tell it to use a particular partition and filesystsem, but specify it to be your root partition (root is symbolised by "/")[/QUOTE]
At no point during the install does it ask for input on where the ramdisk is.
What is really odd, is my downloaded ISO installs fine.
The 'shippit' cd's during the install ask for one of 3 kernel's for you to select, and no matter which kernel I select, I get the the 'bootstrap.log' error message.

---

### Post by az on 2005-11-17
[QUOTE=gabbman]At no point during the install does it ask for input on where the ramdisk is.[/QUOTE]

No, it figures that out by itself.  The point is that once you turn off the computer, the info is gone.  So, if you bootinto the llive cd, you will not find that file.

Did you successfully install?

---

### Post by gabbman on 2005-11-17
[QUOTE=azz]No, it figures that out by itself.  The point is that once you turn off the computer, the info is gone.  So, if you bootinto the llive cd, you will not find that file.

Did you successfully install?[/QUOTE]
But this is not on the live cd, it's from the install cd, so in the base install it still has not had the oportunity to reboot yet.

---

### Post by gabbman on 2005-11-18
yes, but not off the shippit cd's, I had to use the download ISO.

I was not installing off a live cd, but the install cd.

---

