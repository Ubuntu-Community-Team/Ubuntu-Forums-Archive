---
title: "How do I make the windows on my desktop Transparent?"
date: 2006-06-28
forum: Desktop Environments
---

### Post by randell6564 on 2006-06-28
HElLo!

Well...

Once again, I'm Formatting and RE-formatting, trying to come up with the best combination of systems on my box!

I have become a Hardcore Ubuntu fan! (kudo's to all the people involved in creating a Fantastic OS!)

I've been hanging out at gnome-look.org, checking out all the Beautiful artwork created by unix users and noticed some particular screenshots that caught my fancy!

The windows on the desktops of these screenshots were 'Transparent'!

I Love this look and was wondering just how one goes about achieving this!

I dont see a GUI option for this anywhere, so can someone give me a hand?


THANKS!

---

### Post by Maggot on 2006-06-28
The latest and greatest craze is Xgl:

[http://www.novell.com/linux/xglrelease/](http://www.novell.com/linux/xglrelease/)

[http://www.ubuntuforums.org/showthread.php?t=127090](http://www.ubuntuforums.org/showthread.php?t=127090)

That enables you to have transparent windows.  There are other window managers that let you but I cannot remember which ones.

---

### Post by userundefine on 2006-06-28
XGL's what you're after...

---

### Post by randell6564 on 2006-06-28
Thank YOU!

I'm gonna go and check that out right now!

---

### Post by randell6564 on 2006-06-28
[QUOTE=Maggot]The latest and greatest craze is Xgl:

[http://www.novell.com/linux/xglrelease/](http://www.novell.com/linux/xglrelease/)

[http://www.ubuntuforums.org/showthread.php?t=127090](http://www.ubuntuforums.org/showthread.php?t=127090)

That enables you to have transparent windows.  There are other window managers that let you but I cannot remember which ones.[/QUOTE]

OK...

I installed 'Xgl' from Synaptic.  Is it something that I have to run from the terminal?

I dont see it anywhere. (How do ya use it?)

---

### Post by YourDoom123 on 2006-06-29
search the forums. theres a variety of guides depending on your distro/DE/video card. i recommend getting it from the cvs and not from the dapper repos, because the dapper repos are out of date...severely.

---

### Post by randell6564 on 2006-06-29
[QUOTE=YourDoom123]search the forums. theres a variety of guides depending on your distro/DE/video card. i recommend getting it from the cvs and not from the dapper repos, because the dapper repos are out of date...severely.[/QUOTE]

I'm a newb!  "DE" is not something that I am familiar with.  ?  But...

I already installed it.  Also...

What is "cvs"?

---

### Post by randell6564 on 2006-06-29
[QUOTE=userundefine]XGL's what you're after...[/QUOTE]

userundefine, THAT is a Beautiful Screenshot!  So...

Maybe I should ask you this question.  How Exactly do you do it?  I installed xgl.

Is it something that I have to start and use from the terminal?

---

### Post by userundefine on 2006-06-29
Uninstall it with synaptic.  Search the forums depending on your hardware (nvidia/ati) and **d**esktop **e**nvironment (gnome/kde).

CVS is concurrent version system.  Basically it's access to the most recent source code on the project.  IMO it's best *not* to use CVS if you're a newbie, but the Compiz repositories... most of the guides will show you all you need to know.  They're peppered throughout the forums here.

---

### Post by randell6564 on 2006-06-29
[QUOTE=userundefine]Uninstall it with synaptic.  Search the forums depending on your hardware (nvidia/ati) and **d**esktop **e**nvironment (gnome/kde).

CVS is concurrent version system.  Basically it's access to the most recent source code on the project.  IMO it's best *not* to use CVS if you're a newbie, but the Compiz repositories... most of the guides will show you all you need to know.  They're peppered throughout the forums here.[/QUOTE]

ok...

I didnt realize that it was that complicated!  I'll go and search.  I'm useing a ATI Radeon 9200 Graphics card

THANKS!

---

### Post by userundefine on 2006-06-29
The software is in alpha stages right now and installation isn't so user-friendly because of it... nevertheless there are a great many people here who have installed it and can help you.

---

### Post by YourDoom123 on 2006-06-29
[QUOTE=userundefine]U  IMO it's best *not* to use CVS if you're a newbie, but the Compiz repositories... most of the guides will show you all you need to know.  They're peppered throughout the forums here.[/QUOTE]

Sorry i wasn't clear. I meant to use the repos that are built off the cvs code, like beerorkid. thats what most of the guides suggest.

---

### Post by randell6564 on 2006-06-29
Well...

I found this: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Seemed simple enough to follow. (which I did)  But after doing a 'dpkg-reconfigure xserver-xorg', and choosing 'fglrx', then rebooting, nothing seemed to have changed.

Except... when I tryed to confirm that what I did worked, I got nothing but error messeges when entering, 'fglrxinfo' at the command line.

So I guees I'll just have to live with what I have now.

Thanks for all of your help!

---

### Post by Max Luebbe on 2006-06-29
Userundefine, what is the ObjectDock/ Mac Dock looking thing at the bottom of your screenshot called?

---

### Post by randell6564 on 2006-06-29
The 'Kororaa live cd' does'nt work either!  

So... Maybe my ATI card just is'nt beefy enough for xgl!

CRAP!

Heres my system info:

[B]OS Name	Microsoft Windows XP Home Edition
Version	5.1.2600 Service Pack 2 Build 2600
OS Manufacturer	Microsoft Corporation
System Name	SCOTT
System Manufacturer	MICRO-STAR INTERNATIONAL CO., LTD
System Model	MS-7071
System Type	X86-based PC
Processor	x86 Family 15 Model 4 Stepping 1 GenuineIntel ~2666 Mhz
BIOS Version/Date	Phoenix Technologies, LTD 6.00 PG, 11/16/2005
SMBIOS Version	2.3
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.2180 (xpsp_sp2_rtm.040803-2158)"
User Name	SCOTT\BigBoss
Time Zone	Pacific Standard Time
Total Physical Memory	510.48 MB
Available Physical Memory	274.50 MB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
Page File Space	1.22 GB
Page File	C:\pagefile.sys[/B]

I dual-boot so right now, I'm useing my WindowsXP desktop.

I dont have the latest, most up-to-date stuff, but geez! I figure that with an ATI Radeon 9200 Graphics card, I could get 'xgl' to work!

Any Ideas?

---

### Post by Maggot on 2006-06-29
Here's a few shots when I had Xgl with Suse. Sorry they are so big.

[IMG]http://www.mustangmods.com/ims/u/154/1528/56097.jpg[/IMG]

[IMG]http://www.mustangmods.com/ims/u/154/1528/56096.jpg[/IMG]

---

### Post by randell6564 on 2006-06-29
[QUOTE=Maggot]Here's a few shots when I had Xgl with Suse. Sorry they are so big.

[IMG]http://www.mustangmods.com/ims/u/154/1528/56097.jpg[/IMG]

[IMG]http://www.mustangmods.com/ims/u/154/1528/56096.jpg[/IMG][/QUOTE]

OK Maggot,  UR TEASING me now!  Thats not fare! LOL!

What is it about my system that prevents me from getting xgl working?!

Although, I'm not interested in attaining a 3d desktop... I want TRANSPARENT WINDOWS!

---

### Post by userundefine on 2006-06-30
[QUOTE=Max Luebbe]Userundefine, what is the ObjectDock/ Mac Dock looking thing at the bottom of your screenshot called?[/QUOTE]
Starterbar from gdesklets.

---

### Post by userundefine on 2006-06-30
[QUOTE=randell6564]The 'Kororaa live cd' does'nt work either!  

So... Maybe my ATI card just is'nt beefy enough for xgl!

CRAP!

...

I dual-boot so right now, I'm useing my WindowsXP desktop.

I dont have the latest, most up-to-date stuff, but geez! I figure that with an ATI Radeon 9200 Graphics card, I could get 'xgl' to work!

Any Ideas?[/QUOTE]
Your card is adequate enough.  It's just that ATI gives about zero support for Linux, and it's harder to get them working.

Check out [this thread](http://www.ubuntuforums.org/showthread.php?t=131253) and others specific to ATI and XGL.

---

### Post by randell6564 on 2006-06-30
[QUOTE=userundefine]Your card is adequate enough.  It's just that ATI gives about zero support for Linux, and it's harder to get them working.

Check out [this thread](http://www.ubuntuforums.org/showthread.php?t=131253) and others specific to ATI and XGL.[/QUOTE]

Thank You My friend!

---

