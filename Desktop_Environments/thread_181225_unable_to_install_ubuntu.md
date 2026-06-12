---
title: "unable to install ubuntu"
date: 2006-05-23
forum: Desktop Environments
---

### Post by Perfex on 2006-05-23
Ok i Have searched the forums on issues regarding the partitioner, and I have not come up with much

My problem is I will get through to the setup and it will hang at setting up the partitioner, I was able to get past it 2 times by what means I do not know, was going through the install, and it said Base system installation error.. the debootstrap program exiited with an error (return value 1) check /target/var/log/bootstrap.log for details

I am not able to get to this point again, since then I have burnt anther cd with the install of 5.10 at 4x

Is there anyone who has a work around for this issue, or has any suggestions.

on another note I was able to get the live version running on my computer if I Ctrl+ c 
past starting up enterprise volume managment system, and ran just fine.

Thankyou in advance

Things I have done:
unhooked all other usb items but keyboard mouse
unhooked ethernet
burnt a second cd

Specs of my system: 
Athlon xp 2800, Geil Golden Dragon 512x2, Plextor Premium CDRW, Seagate 120 gig sata HD, ATi 9700 pro 128mb video card, 
Soltek SL-75FRN2 Motherboard, PC Power & Cooling Turbo Cool 425 Ultra Deluxe PS

---

### Post by ispmarin on 2006-05-23
Maybe this is some issue with the sata drive. Is there more than one mode in the bios for the sata drive? if it is, what are they? You can try with different modes and sees what happens.

---

### Post by yyagol on 2006-05-23
Hi
I had problems like that before with Fedora but it turned out
my CD's had not been checked before or after burning.
as far as i remember ther is an option to check the cd during installation.

---

### Post by Perfex on 2006-05-23
[QUOTE=ispmarin]Maybe this is some issue with the sata drive. Is there more than one mode in the bios for the sata drive? if it is, what are they? You can try with different modes and sees what happens.[/QUOTE]

It uses a Fastbuild Promise Utility (seperate bios)
its setup mode U5 only option it allows me for 1 drive

---

### Post by Perfex on 2006-05-23
[QUOTE=yyagol]Hi
I had problems like that before with Fedora but it turned out
my CD's had not been checked before or after burning.
as far as i remember ther is an option to check the cd during installation.[/QUOTE]

When ubuntu goes through its initial setup process, it does say checking cd and doesnt show anything, is this what you are refering too?

---

### Post by yyagol on 2006-05-23
Sorrry just trying to help
are you using a SATA or any RAID ?

---

### Post by Perfex on 2006-05-23
[QUOTE=yyagol]Sorrry just trying to help
are you using a SATA or any RAID ?[/QUOTE]

It is setup the only way It can be as far as I know, Array 1 stripe

---

### Post by Perfex on 2006-05-23
Well I atempted to find a diffrent os driver for the fasttrack 376 utility, best I found is [http://www.promise.com/support/download/download2_eng.asp?productId=88&category=all&os=4&go=GO](http://www.promise.com/support/download/download2_eng.asp?productId=88&category=all&os=4&go=GO)

getting this from this post [http://www.linuxcompatible.org/Promise_FastTrack_376378_c11100.html](http://www.linuxcompatible.org/Promise_FastTrack_376378_c11100.html)

still do not know what to do though, does not explain why I was able to get into the partitioner before, and not now.. hmm... im lost

going to reset my bios and try restarting the installation.. will post again soon

---

### Post by Perfex on 2006-05-24
Well was not able to get ubuntu installed on my seagate 120 sata drive, however I did get it installed on an old 30 gig WD drive, seems to run nice.. if anyone ever finds a work around for the problem give me a hollar.

Will be trying both drives installed soon, currently sata is disconnected, will see how it responds, i will probably just change the boot order in the bios when I want to boot to windows/ubuntu.. so far only thing I can think I would use windows for is gaming... Everquest 2, Vanguard whenit comes out, etc.. besides that I ran Gimp in windows for about a year and just started playing with inkscape, very impressed with ubuntu so far, will have to get used to a new file structure, and figure out compiling, etc

---

