---
title: "Vista64 to Ubuntu?"
date: 2009-06-20
forum: General Help
---

### Post by DredBull 30-06 on 2009-06-20
Since this is the help forum I would like to call for some help/opinions with my inquiry.

I am currently using Windows Vista 64-bit and wanting to switch to Ubuntu Beryl 64-bit. I have done some reading but can't make sense of what I would need to do to actually run Ubuntu.

I have used Windows since 95 but in the last 3-4 years I have been thinking of switching to Linux. I came to this forum for some clarity and help if I do decide to make the switch.

What I do understand about Linux is I will need to manually install all of my drivers. Short list I know. Are there any benefits to using Linux other than programming?

The computer I am considering installing Linux on is an HP desktop (Phoenix SE a6655f). The run down is 5GB DDR2, AMD x4 9150e, also a 7900GS with DVI to my 24" Samsung. I play video games online, watch DVDs, listen to music <itunes>, and instant message. Is Linux right for me?

---

### Post by DredBull 30-06 on 2009-06-20
Can anyone give me their two cents worth? Much appreciated.

---

### Post by themusicalduck on 2009-06-20
The best place to start is to download a .iso from [www.ubuntu.com](www.ubuntu.com). Download the desktop edition and it will let you select either 64 bit or 32 bit depending on which you prefer. Ubuntu Beryl isn't an actual version that I know of. Beryl refers to a set of desktop effects which are now replaced by Compiz and come pre-installed in Ubuntu. The latest Ubuntu version is 9.04.

Write the .iso to a CD and then boot into the CD from your bios. You may need to change some settings in your bios or initiate some kind of boot menu to make the computer boot from the CD.

Once it's booted, select a language and then select 'Try Ubuntu without any changes to my computer' This will load you into an Ubuntu session that runs off the CD. It'll be a lot slower than an actual install would be, but you can have a look at the features and what software is pre-installed. Have a look at Add/Remove to see what other software is available (which is under Applications in the top left) and check whether or not all your hardware works well with it. Chances are everything will work straight away without having to change things or install drivers, except for your graphics card. The live session will run in low graphics mode and probably low resolution, but if you decide to install Ubuntu then you can have the NVidia drivers installed automatically for you afterwards.

If you decide you want to install, then click on the Install icon on the desktop and it will take you through the setup. There's an option to install Ubuntu alongside Vista and run as a dual-boot if you like or an option to 'Use entire disk' ONLY if you want to replace Vista and have a completely new machine. It's probably worth backing up vital bits of data off your drive first, because you will be doing some re-partitioning.

As for what you want to do with Ubuntu, there are pieces of software that'll work for you. You can watch DVDs, but you will need to install codecs first which can be downloaded automatically for you. A good itunes replacement is either Amarok or Songbird (Amarok is my favourite). There are many MSN clients available or Pidgin is pre-installed, which supports many chat protocols.

As for video games online, flash works fine in Ubuntu. If you mean online multiplayer games, there isn't a massive selection on Ubuntu but there are some games. However if you'd like to install a Windows game then you may be able to use Wine to run it in Ubuntu. [http://www.winehq.org/](http://www.winehq.org/) and you can look up the program to see how well it runs at [http://appdb.winehq.org/](http://appdb.winehq.org/).

If you need any more help with anything then we're happy to help.

---

### Post by Ayuthia on 2009-06-20
You should not have to install your drivers manually with the exception of graphics card and wireless network cards.  You will most likely be able to activate your graphics card driver by going to System->Administration->Hardware Drivers and activating it, but the hardware icon might even appear on the panel for you to activate it.

The next hurdle would be to get your music and DVD's to play because of the installation of the codecs.  This is pretty much a matter of going to the Medibuntu site and following the instructions there.

Video games might be the only difficulty if you are referring to Windows online gaming.  Some of them can be handled through some Linux applications but some can't.

The best bet would be to install it via Wubi.  It will create a file in Windows where Ubuntu will live.  You can try it out and see if you like it.  If you do, you can then take the next step of creating a partition and dual boot Windows and Ubuntu.

One of the nice things with Linux is with web browsing.  Since Linux is not really popular yet, not too many viruses and spyware are geared towards it so your system will not get bogged down by those issues.

Of course, Linux is not Windows so you will need to understand that you will need to give it some time to get comfortable in it.  Not everything is in the same place as Windows and the look and feel will be different.  However, there is a friendly Ubuntu forum community here that will be more than happy to help you out when you are stuck.

---

### Post by nmaster on 2009-06-20
TRY WUBI!!!!! [http://wubi-installer.org/](http://wubi-installer.org/)

You don't have to worry about partitions or anything.  You can see how your hardware drivers work out.  I've been using wubi for about a month and a half.  I'm ready to move to Jaunty, but I don't want to take any risks at the moment (I really need my laptop for work).  I'm very conservative, you don't have to stick with wubi for so long, but you should at least try it out for a few weeks.  It'll give you more time to learn about using ubuntu and you'll still have Vista to fall back on to if you need something more familiar.  Another great thing is that if you mess something up, you can just uninstall from Control Panel.

Down sides:  
1. Wubi isn't quite as fast as an actual install, but I haven't had any problems.
2. You can't use hibernate.

---

### Post by Sef on 2009-06-20
> You should not have to install your drivers manually with the exception of graphics card and wireless network cards. 

Graphics Cards: If you want 2D, then the installed drivers will work just fine.  For 3D, you need to install proprietary drivers.

Wireless Network Cards: They may or may not work out of the box.

---

### Post by 3rdalbum on 2009-06-21
> **DredBull 30-06 said:**
> Since this is the help forum I would like to call for some help/opinions with my inquiry.

I am currently using Windows Vista 64-bit and wanting to switch to Ubuntu Beryl 64-bit. I have done some reading but can't make sense of what I would need to do to actually run Ubuntu.

Okay, it's just "Ubuntu 64-bit". Beryl is an old piece of software that used to run on Ubuntu. The graphical effects provided by Beryl are available on standard Ubuntu.

It's very easy to actually run Ubuntu. Get a copy of Ubuntu, either by downloading an ISO disk image of it and burning to disk, or by using the Shipit service ([http://shipit.ubuntu.com](http://shipit.ubuntu.com)) to order a free disk. Ubuntu is included on many computer magazine coverdisks too.

Once you have an Ubuntu CD, you need to change one setting in your BIOS, so that it checks the CD drive for bootable disks BEFORE it starts up from hard disk. In the first few seconds after you start up, the computer will say something like "<F2> Boot Order" or "Press DEL to enter Setup", telling you what key to press in order to enter the little program that lets you change the boot settings.

Then put the Ubuntu CD in, restart the computer and follow the instructions onscreen. It's all point-and-click.

> What I do understand about Linux is I will need to manually install all of my drivers.

Not at all - Linux comes with drivers for most things and will automatically use them on startup. If you want 3D acceleration from your graphics card, you will need to install the Nvidia proprietary driver. This is as easy as running a program included with Ubuntu, that will download and install the driver for you.

Speaking of that, your graphics card is capable of running desktop effects quite well, but for the really spectacular stuff you would need a better card.

> Are there any benefits to using Linux other than programming?

Absolutely. There are no viruses on Linux, and the system has always been designed for security. All operating system and software updates are free and will always be free. Your Linux computer won't do anything sneaky like "phone home" or give away personal information to third parties. The whole Linux system makes more sense to me than Windows does, and there are a lot fewer things about Linux that annoy me - you might have the same experience.

Linux doesn't require maintanence like defragmenting the hard disk or "cleaning the registry", and it does not get slower the longer you use it. The Gnome desktop interface used in Ubuntu is easy to use for new and experienced users, and never feels intimidating.

You can get deep into the system if you like, swap out parts of the system for the latest and greatest - or you can just use it all day, every day without fear that it will fall over. Linux is exciting - there's always something new in the pipeline that you will be able to experience in semi-completed form in the next six-monthly release of Ubuntu, or you can install it today even while it's in heavy development.

Linux programs conform to open standards, so you are never locked to a piece of software by the fear that you'll lose access to your documents by switching to another piece of software.

You might not understand some of these reasons why I (a non-programmer) like Linux, but if you start using it you might understand what I mean. I also have a romantic perception of Linux as being "the people's operating system" - anybody can contribute to the community and any programmer can work to make the system better. Linux is always what Linux users want it to be. Doesn't that sound exciting?

> The computer I am considering installing Linux on is an HP desktop (Phoenix SE a6655f). The run down is 5GB DDR2, AMD x4 9150e, also a 7900GS with DVI to my 24" Samsung. I play video games online, watch DVDs, listen to music <itunes>, and instant message. Is Linux right for me?

That can all be done. If you have DRM-encrypted music that you've bought from the iTunes music store, you must unprotect it before you will be able to use it on Linux. (For a small fee Apple can decrypt and deprotect your music, or there are illegal programs around for Windows that can do it, or you can simply use iTunes to burn it to CD).

Linux cannot run Windows programs (well, it can run a small number of them with some software called Wine), just as Windows cannot run Linux programs. A lot of familiar open-source software for Windows is also available for Linux. But, as such, your Windows games might not run (some can). This isn't necessarily a show-stopper, as there are some pretty good Linux games out there, and you can install Linux alongside Windows so you can just "boot into Windows" if you want to play an incompatible game.

---

### Post by DredBull 30-06 on 2009-06-21
Thank you all for helping me out with this. I am going to try the "boot from disc" option just to see if it is idiot friendly before I do a full install and get rid of this Vista.

I have requested the free CD but it is asking to wait 4-6 weeks for delivery.

I tried to make a CD by downloading the desktop version and burning it as an ISO. The short version of my confused 3 hour story -I am completely lost-, I downloaded the "ubuntu-9.04-desktop-amd64" file from this site as well as DeepBurner and InfraRecorder to get it into a .iso file (or I was hoping to anyways) so I can boot from disk. The first time I tried burning the disk, I burned just the "isolinux" folder onto a 700mb cd. No luck.

I have read and followed the instructions from the tutorials given to making such a disk and the only thing it did for me was waste my time, one link led to another and back to the start. It doesn't explain that I need a .iso file in the first place to make a .iso disk. The download doesn't even have a single .iso file in all of it's 696mb. Or even if you don't need a .iso file to make a boot disc. Do you just burn the entire download onto a disc after it is extracted?

I apologize if I sound like "just another noob" kind of person but just burning the install/boot disk got the better of me. If anyone has a tip or two about burning a boot disc from the download I am "all eye's" but I completely understand if you don't have the time and I will have to wait the 4-6 weeks.

Thanks again to the great people that have helped me get this far. The help is appreciated.

---

### Post by Legace on 2009-06-21
Go to [http://isorecorder.alexfeinman.com/Vista.htm](http://isorecorder.alexfeinman.com/Vista.htm) and download the 64-bit version (you are using 64-bit, right?)

Once you've installed it, insert a blank CD/DVD in your drive, then right-click on the **ubuntu-9.04-desktop-amd64.iso** and select **"Copy image to CD"**.

[img]http://www.ubuntu-fi.org/images/levykuva-isorecorder/isor7.jpg[/img]

Then just press Next, and once its done, reboot, and boot off your CD ;)

---

### Post by kelvin spratt on 2009-06-21
No you don't extract the iso file you write the image to disc try right clicking on the iso file
and see if something like (write image to disc appears) it does with windows7 if so use a good brand of CD burn at a low speed.
 If not download [http://www.imgburn.com/](http://www.imgburn.com/) its made for iso files and its free. Remember you are writing image to disc and you should not go wrong.
 Also I feel if you can't get over this part how are you ever going to install if you decide to install to your hard disc, this is not meant as a jibe at you but to do more research 1st

---

### Post by 3rdalbum on 2009-06-21
From what I hear, Windows will either believe that the ISO file you downloaded (you know, the 696mb file) is a RAR and will try to open it in WinRAR, or it will give you the option of opening it as though it was a folder.

Don't do either.

Just use your favourite burning software to burn that single file to a disc, **as a disc image**. The setting in the burning software is usually called "Burn image to disc" or "Burn ISO image".

Some software has an option like "Make a bootable disc" - that is something completely different and not what we want.

---

### Post by DredBull 30-06 on 2009-06-21
> **3rdalbum said:**
> From what I hear, Windows will either believe that the ISO file you downloaded (you know, the 696mb file) is a RAR and will try to open it in WinRAR, or it will give you the option of opening it as though it was a folder.

Don't do either.

Just use your favourite burning software to burn that single file to a disc, **as a disc image**. The setting in the burning software is usually called "Burn image to disc" or "Burn ISO image".

Some software has an option like "Make a bootable disc" - that is something completely different and not what we want.

Thanks man this made sense to me and right after I read it I right clicked the file I downloaded and checked the properties thinking it was a .zip folder and turns out it is the .iso. It was showing a winrar icon beside it with no format in my downloads folder so I automatically thought to extract it and look for the .iso. That is what drinking RdBll and staying awake for 30 hours does to you kids.

Thank you people for helping me out with this.

---

### Post by 3rdalbum on 2009-06-21
> **DredBull 30-06 said:**
> It was showing a winrar icon beside it with no format in my downloads folder so I automatically thought to extract it and look for the .iso.

Yeah, it's a bug in Windows, and it misleads many users. Unfortunately it's easier for a camel to pass through the eye of a needle than it is to actually report a bug to Microsoft! :-)

I'm glad we've solved your problem today.

---

### Post by egalvan on 2009-06-21
> **kelvin spratt said:**
> No you don't extract the iso file you write the image to disc...
 use a good brand of CD burn at a low speed.

download [http://www.**imgburn**.com/](http://www.**imgburn**.com/)
 its made for iso files and **its free. **


+1 for imgburn.

It's a great piece of software.


Now onto my soapbox...

Yes, the software is free, but the author does accept donations.

So if you use it, and it helps you...even one time...

then toss the author a buck or three.

Help support quality stuff.

Me, I donate $10 on a yearly basis, because it's worth it to have a small, well-written program on a flash drive,
 ready to install any time I need to burn an .iso on a Microsoft machine.

EGalvan

---

### Post by oldos2er on 2009-06-21
> **DredBull 30-06 said:**
> Since this is the help forum I would like to call for some help/opinions with my inquiry.


 Here're some links to help get you started:

 [https://help.ubuntu.com/9.04/newtoubuntu/C/index.html](https://help.ubuntu.com/9.04/newtoubuntu/C/index.html)

 [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

 [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

