---
title: "K3b"
date: 2005-05-29
forum: Desktop Environments
---

### Post by spencer on 2005-05-29
I have a whole bunch of mp3 files on my drive that I want to backup. I have a Cendyne 48X16x48 CD/RW on this Gateway E-3400 1Ghz 512 MB. if this info helps. I've tried using k3b and gnomebaker, niether works. Will the Cendyne burner  work with k3b or gnomeBaker? 

-spencer

---

### Post by clb137 on 2005-05-29
[QUOTE=spencer]I have a whole bunch of mp3 files on my drive that I want to backup. I have a Cendyne 48X16x48 CD/RW on this Gateway E-3400 1Ghz 512 MB. if this info helps. I've tried using k3b and gnomebaker, niether works. Will the Cendyne burner  work with k3b or gnomeBaker? 

-spencer[/QUOTE]


Hi,

Why do they not work?  can u be a little more specific with the reason for not working?

I do not have a problem with any of the program,  


clinton

---

### Post by spencer on 2005-05-29
Sorry about that, I guess I shouldn'tt expect anyone to read my mind on this one without a little more info.   I've haven't had much sleep and am a little slow at the moment. I'll try and get it together and be a little more specific here.

When I try to erase cd/rw with k3b it just says that it is erasing disk but it never completes and it shouldn't take as long as it has to erase disk, same thing happens with GnomeBaker. 

I think I may have a problem as I just logged out of Ubuntu and receive an "Error! Failed to initialize HAL!" message. Searched the Ubuntu forums and read another post regarding this same error message. It's somehow related to a bad burner I assume. Thing is, is burner works in XP drive ok. I hope this make sense now.

-spencer

---

### Post by clb137 on 2005-05-29
Spencer,

Have you made sure that all the files have been installed with your burining programs?  Not sure why nothing is working, sometimes i will have a small problem with one of the programs,  but i find that Gnomebaker works the best in Gnome.

Which desktop are u using?

clinton

---

### Post by spencer on 2005-05-29
When I installed k3b I also installed all the associated files along with it. They are as follows:

k3b-
k3blibs
kcontrol
kde base-data kedlibs-bin
kdelibs-data
kdelibs4
libarts1
libflac++4
libnetpbm10
libopenexr2
libpcre3
libqt3c102-mt
menu-xdg
netpbm


I'm using Ubuntu with Gnome. Do I need KDE desktop to run k3b? 

GnomeBaker should work since I'm using Gnome. Not sure what associated files I need for GnomeBaker.

-spencer

---

### Post by derrick1985 on 2005-05-29
[QUOTE=spencer]When I installed k3b I also installed all the associated files along with it. They are as follows:

k3b-
k3blibs
kcontrol
kde base-data kedlibs-bin
kdelibs-data
kdelibs4
libarts1
libflac++4
libnetpbm10
libopenexr2
libpcre3
libqt3c102-mt
menu-xdg
netpbm


I'm using Ubuntu with Gnome. Do I need KDE desktop to run k3b? 

GnomeBaker should work since I'm using Gnome. Not sure what associated files I need for GnomeBaker.

-spencer[/QUOTE]

No, you don't need kde to run k3b, i use it, never with a cd-rw though.

You also need cdrdao, sudo apt-get install cdrdao and reboot and try that.

---

### Post by spencer on 2005-05-29
I did install cdrdao still no luck. Yes, you are right k3b does work without kde. I have another pc with Ubuntu on it and have successfully burned cdrw's with it. I can't figure this one out. Anyone have a suggestion on how I can backup all those mp3 files if I don't get the burners to work? I don't want to lose them.

-spencer

---

### Post by clb137 on 2005-05-29
[QUOTE=spencer]I did install cdrdao still no luck. Yes, you are right k3b does work without kde. I have another pc with Ubuntu on it and have successfully burned cdrw's with it. I can't figure this one out. Anyone have a suggestion on how I can backup all those mp3 files if I don't get the burners to work? I don't want to lose them.

-spencer[/QUOTE]


2 network cards and a crossover cable,  connect the machines togeather and move your data to the good machine and burn away.

clinton

---

### Post by spencer on 2005-05-29
Yes, I could do the network connection thing, however it doesn't give me a solution with backing up my data and running a burner in ubuntu on this machine. I'm afraid I may have to start from scratch to see if it fixes it. thanks.

-spencer

---

### Post by spencer on 2005-05-30
Before I start from scratch I thought of the obvious, which is to uninstall K3b and GnomeBaker. I have all the associated files that are required for K3b but not Gnome. Where can I find a list of these? Thanks.

-spencer

---

### Post by clb137 on 2005-05-30
[QUOTE=spencer]Before I start from scratch I thought of the obvious, which is to uninstall K3b and GnomeBaker. I have all the associated files that are required for K3b but not Gnome. Where can I find a list of these? Thanks.

-spencer[/QUOTE]


Hi Spencer,

Using synaptic to install program there you can instruct it to smart install, this will install all the required files



clinton

---

### Post by spencer on 2005-05-30
Is the smart install option in preferences? or do you mean just install k3b using synaptic and it will automatically give you a list of dependencies?

-spencer

---

### Post by clb137 on 2005-05-30
[QUOTE=spencer]Is the smart install option in preferences? or do you mean just install k3b using synaptic and it will automatically give you a list of dependencies?

-spencer[/QUOTE]


Spencer,

When you 1st run the program it should give you the option, from then on it will allways smart upgrade

clinton

---

### Post by spencer on 2005-05-30
Thanks,

I don't remember if I checked the smart upgrade first time I ran synaptic or not. I don't remember the option for it. Anyway, I finished reinstalling k3b and am getting ready to try one more time. we'll see what happens. Thanks.

-spencer

---

### Post by clb137 on 2005-05-30
[QUOTE=spencer]Thanks,

I don't remember if I checked the smart upgrade first time I ran synaptic or not. I don't remember the option for it. Anyway, I finished reinstalling k3b and am getting ready to try one more time. we'll see what happens. Thanks.

-spencer[/QUOTE]

Good luck,

which desktop are you using????

clinton

---

### Post by VyRuZ on 2005-05-30
I wanted to share with you some things before you switch Distro's ....

I got an LITE-ON DVDRW SOHW-1653S which works flawlessly on Winblowz , with both Nero 6 Enterprise and Alcohol120% ...
Switched to Kubuntu and i first tried K3B to burn my data ... First i needed to Erase a CD-RW... It did not work , or so i thought ... It was taking so long i rebooted my machine and then because of some errors i reinstalled Kubuntu :P

Next i was afraid to try erasing in K3B again so i got gnomebaker with Konsole ( [http://www.ubuntuguide.org/#gnomebaker](http://www.ubuntuguide.org/#gnomebaker) ) 

I erased the disc in GnomeBaker using Fast Erase and it worked perfectly ...
But Gnome can't burn my disc's because it wants to image everything it burns ...
So i went back to K3B. Burned some data with it in the wrong format , and my home cinema wouldn't understand the MP3's on it , so i had to erase the disc again , in GnomeBaker ... This time I forgot to check the Fast Erase . Man was i scared ... It took friggin' 30minutes to erase that 700mb cd with only 80MB written data on it !! I was so scared , but i left it going ... Finally it actually erased it ...

So i dunno if it's actually a hardware problem , but the writing/erasing in Kubuntu is REALLY slow ... Dunno why ...
Hope you understood what i was trying to say and you can use this :D

---

### Post by spencer on 2005-05-30
As I suspected, it didn't work, same dead end. Well, I learn the hard way I guess. Sure am learning a lot about linux though. I still have a long way to go. I have Gnome on this machine, my other machine has  Gnome, kde, and xfce. 

Thank you too "VyRuZ", for your info. You may be right on this one. As I said earlier in the thread I had an error message "Error! Failed to initialize HAL!" seems that is related to hardware confusion. Well I'm through for now, I've been at this forever. I'll try again later. I really want to avoid losing all those mp3 files as well as some other important data. Thanks, till next time.

-spencer

---

### Post by spencer on 2005-06-03
Hello again,

I did manage to backup all my data to zip disks on my machine and I have not reinstalled ubuntu. I really don't want to but this is bugging me, why I am not able to burn to cd? Everything else works great but this. I get the following error in GnomeBaker when I try and erase cd/rw: 

```
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
resid: 64512
``` 

What is the translation on this? Anyone?

-spencer

---

