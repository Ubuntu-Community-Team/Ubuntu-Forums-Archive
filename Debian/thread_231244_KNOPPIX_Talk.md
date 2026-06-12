---
title: "KNOPPIX Talk"
date: 2006-08-03
forum: Debian
---

### Post by RAV TUX on 2006-08-03
I have decided to install Knoppix on my hard drive following the procedure below from here:

[http://www.freenet.org.nz/misc/knoppix-install.html](http://www.freenet.org.nz/misc/knoppix-install.html)

> Installation Procedure
 To get Knoppix installed onto your hard drive: 
Boot the Knoppix CD.

 
When the boot prompt comes up, choose your language.
 Most of us speak English, so we'll type: 
boot: knoppix lang=en
 then press ENTER (you don't type the 'boot:' part, of course)

 
Wait till the system is fully launched, including the KDE desktop

 
Press CTRL-ALT-F1, to get a root console. You should see a shell prompt

 
Type: knoppix-installer

 
Follow the guided installation menus. This will include:
 
 
Creating a Linux partition (at least 2.5GB
Creating a Linux Swap partition (at least 256MB)
'Mounting' the Linux partition as root
Initialising the swap partition
Copying all the required files (automatically)
Setting up networking
Setting passwords
Setting up the bootloader (Note: take care with this stage - it could render your system incapable of booting into Windows. If you really need Windows, then it might be a good idea to set up GRUB Bootloader  with a 'chainloader' entry, so that you can dual boot. Working this out is an exercise left to the reader - there are too many possible scenarios for me to cover in this short guide. Also see man grub and the files in /usr/share/doc/grub)
Rebooting (without the CD)

 
When you've rebooted Knoppix from your hard disk, click on the KDE Control Centre icon in the launcher at the bottom of the screen (icon of a colour monitor with a card in front of it)

 
Within the Control Center, click on Personliche Einstellungen

 
Click on Land und Sprache

 
Choose the locale and language of your choice

 
Click on Andwenden at bottom of that window

 
Close and restart the Control Center

 
Click on Peripherals, then Keyboard, and choose your preferred keyboard layout (which will probably be US.English. Click OK and close the window

 
Press CTRL-ALT-F2 to get to the root console, and log in as root (using the password you chose when you ran the installer)

 
(Optional) - type apt-get update (followed by ENTER). This will update your list of available packages, and takes about 5-10 minutes.

 
Hey, presto, you've got a fully installed GNU/Linux desktop

 
From here on in, you'll probably want to fine-tune a few things, set up themes, backgrounds etc. But most of the hard work is already done for you!
And lastly, note that Knoppix is based on Debian, which is arguably the finest GNU/Linux infrastructure available. To learn more about your system, and how to add/change/remove software, go to the Debian website and read the documents. If you get really stuck, start up X-Chat and log into irc.debian.org or irc.openprojects.net and join channel #knoppix. That is one busy chat room, with Debian Linux experts present 24/7, willing to help. Please also know that, even though Knoppix is based on the Debian distribution, your enquiries in #debian may not be welcomed.

I will post progress or set backs and ask: if you have experience installing Knoppix please post advice and your experience.

Jozef

---

### Post by crxyem on 2006-08-03
cool you installed knoppix, but wouldn't you think that this would be better suited for a knoppix based forum vs ubuntu ??

---

### Post by cantormath on 2006-08-03
HEY!!!!!
Any anyone using linux, even if it has nothing to do with this forum, is welcome to post that they are using linux.

Howtos of any distro should be welcome, except vista ::grin::

HI-5! for knoppix

---

### Post by Iandefor on 2006-08-03
> **cantormath said:**
> HEY!!!!!
Any anyone using linux, even if it has nothing to do with this forum, is welcome to post that they are using linux. Even better, we don't care who posts, as long as they obey the forums rules and post in the right forums... as yozef just did ;).
> 
Howtos of any distro should be welcome, except vista ::grin:: Vista is a Linux-based operating system now ;)?

---

### Post by basketcase on 2006-08-04
why are you installing it?  

I have to tell you though, I LOVE 5.0.1 Live CD!!

---

### Post by rattlerviper on 2006-08-04
Someone always has to try and cause a problem. Anyways let us know how Knoppix turns out. I have been intrested in it for awhile, but just hasn't made it to the top of my list yet.  You recomendation could move it to the top, or erase it from the list altogether(and it is a LONG list).

---

### Post by RAV TUX on 2006-08-04
well Knoppix is not at all easy to install. I met failure.

Easier was the Musix install which gives you 3 choices for a HD install 

1. debian
2. beginer
3. knoppix

great install btw the way the only thing is the grub bootloader didn't work.

so I moved to Dreamlinux

great partitioner and install, but again grub bootloader didn't work.

so I have returned to installing Ubuntu 

(keep in mind I have two computers, one I always have Ubuntu, the other I currently have nothing thanks to FreeBSD)

my only problem with Ubuntu is I am having problems with the install. I will start a thread on this in the proper forum.

---

### Post by RAV TUX on 2006-08-05
The Musix installer is the Knoppix installer I am trying knoppix again.

In fact I just installed it:

here is a screenshot of the install in process:
[IMG]http://img263.imageshack.us/img263/1817/snapshot1ly3.png[/IMG]


to start the Knoppix installation is actually the easiest I have ever seen:

once you boot the live CD 

open the 'Root Shell'

type in 

knoppix-installer

it's that easy...

now I will reboot...lets hope it all works

---

### Post by RAV TUX on 2006-08-05
I went to boot and got Error 21 from GRUB?

---

### Post by RAV TUX on 2006-08-06
error 21 fixed by adjusting the BIOS,  RAID directive btw the best way to install Knoppix is:

to start the Knoppix installation is actually the easiest I have ever seen:

once you boot the live CD 

open the 'Root Shell'

type in 

> INGNORE_CHECK sudo knoppix-installer

it's that easy...

Knoppix has by far the easiest and best installer I have experienced...

I would say my top three installs are:

1. Knoppix
2. Gentoo
3. Morphix

I would say these three are nearly tied for the top position as my favorite installs

but I would say Knoppix is the best.

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***Knoppix Tech Talk***

threads merged:

[http://www.ubuntuforums.org/showthread.php?t=229005](http://www.ubuntuforums.org/showthread.php?t=229005)
[http://www.ubuntuforums.org/showthread.php?t=231244](http://www.ubuntuforums.org/showthread.php?t=231244)

---

### Post by RAV TUX on 2006-08-07
This includes Kinneret which is based on Knoppix

---

### Post by basketcase on 2006-08-08
My quesiton is....

How is the performance based on the Live CD to the Installed Version?

I know my Knoppix Live 5.0.1 was *VERY* quick...

---

### Post by RAV TUX on 2006-08-08
It is even faster....It is faster being installed

---

### Post by basketcase on 2006-08-08
Could possibly be my new favorite distro short of a few pieces of hardware that does not work that Ubuntu currently supports out of the box.

---

### Post by RAV TUX on 2006-08-12
I have a few question here:

1. how to install ubuntu in knoppix

2. how to get gnome working

after doing a lot of gnome-type installs through synaptic package manager.... 

I rebooted, what would normally would be a fast boot got interupted with a problem with Xserver....

here is the message:
> 
GDM: X server not found: /usr/x11r6/bin/x :0 -dpi 96 -audit 0 -auth /var/

Error command could not execute

please install the x server or correct GDM configuration and restart GDM

after this I sign in and type startx to start in KDE....

I really would 

1. prefer gnome
2. would like to get rid of this stalling message.

---

### Post by Cariboo1938 on 2006-08-12
> **yozef said:**
>  

Knoppix has by far the easiest and best installer I have experienced...

I would say my top three installs are:

1. Knoppix
2. Gentoo
3. Morphix

I would say these three are nearly tied for the top position as my favorite installs

but I would say Knoppix is the best.I'm also interested in Knoppix and I wonder what repositories Knoppix uses? Is it Debian based? Does it have an easy to handle Partitioner?

---

### Post by RAV TUX on 2006-08-12
> **Cariboo1938 said:**
> I'm also interested in Knoppix and I wonder what repositories Knoppix uses? Is it Debian based? Does it have an easy to handle Partitioner?

yes Debian based, and you can even install a Ubuntu base (doing that now)....

very easy to handle partitioner;)

the most superior HW detection.

---

### Post by RAV TUX on 2006-09-24
> **Cariboo1938 said:**
> I'm also interested in Knoppix and I wonder what repositories Knoppix uses? Is it Debian based? Does it have an easy to handle Partitioner?

In the Knoppix repositories are both Debian and Ubuntu, which you use through the Synaptic Package Manager, since it is Debian based, you'll find it very similar to Kubuntu.

the install and the partitioner are very easy....

to install Knoppix, after booting to the live CD, open the Knoppix Root Shell and type :

> 
IGNORE_CHECK=1 sudo knoppix-installer

follow the prompts from there for installation and partitioning

---

### Post by Sef on 2006-10-07
I have a friend with a bad hard drive. (It doesn't boot up.) I can access the hard drive through Knoppix, but how do I move the files from the hard drive to a floppy disk?

(His files are small and should all fit on one floppy disk.)

His computer has Windows 98 first edition, 500 MHz, and 192 ram; it's his company's, so he hasn't been able to get a newer Windows.

---

### Post by aysiu on 2006-10-07
Knoppix doesn't recognize the floppy drive?

Is that the only backup medium available? You don't have an iPod or flash drive?

I guess worse case scenario--you could always email the files if they're that small... or repartition the drive and copy the files to a new partition.

---

### Post by odinfromvalhalla on 2006-10-07
you should mount the floppy device 1st.

```
mount /dev/fd0 /mnt
```

then you can copy the files into the /mnt folder.

after you finish to copy the files you can umount the floppy device and get your floppy out!

```
umount /dev/fd0
```

---

### Post by RAV TUX on 2006-10-07
If you are like me and have advanced hardware, alot of main distros will not detect my hardware, incuding but not limited to Ubuntu and Debian.

I currently use Debian, but since Debian will not detect my hardware I have to use Knoppix to install Debian to my harddrive.

Why Debian and Ubuntu don't use the superior hardware detection of Knoppix is beyond me?

anyway, download and burn the latest Knoppix version 5.0.1

upon booting to the live CD, once the KDE desktop is up, go to your main menu>Knoppix>Root Shell> type:

> IGNORE_CHECK=1 sudo knoppix-installer

then follow the simple prompts to partition(if needed) and install

you will be given 3 options to install on your hard drive:

1. Debian
2. Beginner (also Debian)
3. Knoppix (like live CD)

If you have older hardware and Debian detects and installs fine, then stick with Debian, but if you have advanced hardware just use Knoppix.

I also find one CD with Knoppix, is much more efficient then 3 DVD's of Debian.

---

### Post by tturrisi on 2006-10-09
Just curious, what hardware doesn't Debian install detect for you?  And are you referring to Sarge, Etch or Sid Debians?  My laptop is a couple yrs old, a P4 3.02, sis chipset, and Etch detects everything and installs fine.  The onboard wifi is not detected by any distro, including Knoppix, so I use pcmcia wlan cards.  I also have other less-than-a-year-old systems & Etch detects all hardware.

---

### Post by hey_ian on 2006-10-09
> **tturrisi said:**
> Just curious, what hardware doesn't Debian install detect for you?  And are you referring to Sarge, Etch or Sid Debians?  My laptop is a couple yrs old, a P4 3.02, sis chipset, and Etch detects everything and installs fine.  The onboard wifi is not detected by any distro, including Knoppix, so I use pcmcia wlan cards.  I also have other less-than-a-year-old systems & Etch detects all hardware.

Knoppix is based up on all Debian distro, including packages of SID, Sarge and the upcoming Etch.
In my opinion you should use [Kanotix]("http://www.kanotix.com") if you have any problems detecting your hardware. Kanotix is Debian SID combined with Knoppix technology. Kanotix can be called as a very very advanced version of Knoppix, optimized for HP install. Knopper himself is also always in our #kanotix IRC chat and supports the development of Kanotix. Knoppix is not made for HD install.

---

### Post by krypto_wizard on 2006-10-10
I have heard good things about Knoppix and last week when my hard disk crashed I could recover lot of data using Knoppix Live CD.

My question is if Knoppix can be installed as a regular OS as we do other variants of Linux ?

Thanks

---

### Post by moore.bryan on 2006-10-10
*the [knoppix website]("http://www.knoppix.net") talks about how to install and the fact it's basically just a straight debian install with kde.*

---

### Post by RAV TUX on 2006-10-10
> **krypto_wizard said:**
> I have heard good things about Knoppix and last week when my hard disk crashed I could recover lot of data using Knoppix Live CD.

My question is if Knoppix can be installed as a regular OS as we do other variants of Linux ?

Thanks

actually Knoppix has the best installer (IMHO)

from the live CD KDE Knoppix desktop>go to your main menu>Knoppix>Root Shell>

type:
> 
IGNORE_CHECK=1 sudo knoppix-installer

Follow the prompts for partitioning and installing:

you will be given 3 options:

1. Debian
2. Beginner (still Debian)
3. Knoppix (like live CD)

try all three, Knoppix is the best way to install Debian, I have tried every release of Debian and it still does not have good hardware detection or proper drivers, Knoppix basically has this covered.

Good luck and enjoy, The Knoppix Live CD is awesome and the Knoppix Installer is the best way to install Debian to your hard drive

Jozef

---

### Post by krypto_wizard on 2006-10-11
Thank you...that answers my question.

> **yozef said:**
> actually Knoppix has the best installer (IMHO)

from the live CD KDE Knoppix desktop>go to your main menu>Knoppix>Root Shell>

type:


Follow the prompts for partitioning and installing:

you will be given 3 options:

1. Debian
2. Beginner (still Debian)
3. Knoppix (like live CD)

try all three, Knoppix is the best way to install Debian, I have tried every release of Debian and it still does not have good hardware detection or proper drivers, Knoppix basically has this covered.

Good luck and enjoy, The Knoppix Live CD is awesome and the Knoppix Installer is the best way to install Debian to your hard drive

Jozef

---

### Post by hey_ian on 2006-10-11
In my opinion you should use Kanotix if you have any problems detecting your hardware. Kanotix is Debian SID combined with Knoppix technology. Kanotix can be called as a very very advanced version of Knoppix, optimized for HP install. Knopper himself is also always in our #kanotix IRC chat and supports the development of Kanotix. Knoppix is not made for HD install.

---

### Post by cunawarit on 2006-10-11
I haven't had problems with either Debian, Ubuntu, Knoppix, or DSL detecting hardware. But my machines are fairly basic budget things.

Excuse the silly question, but is there anything in particular stopping Debian using the Knoppix hardware detection? Everyone says it is excellent, so why don't more distros use it?

---

### Post by RAV TUX on 2006-10-11
> **cunawarit said:**
> I haven't had problems with either Debian, Ubuntu, Knoppix, or DSL detecting hardware. But my machines are fairly basic budget things.

Excuse the silly question, but is there anything in particular stopping Debian using the Knoppix hardware detection? Everyone says it is excellent, so why don't more distros use it?

this is a good question....

another perspective is why doesn't the Knoppix Installer include more distros....

Keep in mind when you use the LiveCD of Knoppix, when go to install on your hard drive, you install Debian...

I would like to see Ubuntu, and even Kanotix added to the Knoppix Installer....

One Live Distro to rule them all....imagine bringing the major Debian derivatives together with one Live CD, The Knoppix Installer is the first step in the right direction...

then new people would only need Knoppix and from Knoppix they could install Debian (like they currently can) or install Ubuntu, Kanotix, etc....

bringing all development projects together in one commmon effort

---

### Post by RAV TUX on 2006-10-11
> **hey_ian said:**
> In my opinion you should use Kanotix if you have any problems detecting your hardware. Kanotix is Debian SID combined with Knoppix technology. Kanotix can be called as a very very advanced version of Knoppix, optimized for HP install. Knopper himself is also always in our #kanotix IRC chat and supports the development of Kanotix. Knoppix is not made for HD install.

I have been using Knoppix (Debian installed with the Knoppix installer) on my hard drive for months...

after reading all the goods things people said about Kanotix, which I understand has a strong fan base, I am sorry to say I was sadly disappointed overall,...

---

### Post by xXx 0wn3d xXx on 2006-10-11
I have 2 simple questions:

Does Knoppix use the offical debian repositories, or does it use it's own repositories ? If it uses it's own, how well maintained are they ?

and:

Can Knoppix use Ubuntu packages ? (I am assuming no but I wanted a definite answer.)

---

### Post by Sef on 2006-10-11
> I have been using Knoppix (Debian installed with the Knoppix installer) on my hard drive for months...

after reading all the goods things people said about Kanotix, which I understand has a strong fan base, I am sorry to say I was sadly disappointed overall,...

What were you disappointed about with Kanotix?

---

### Post by RAV TUX on 2006-10-13
> **xXx 0wn3d xXx said:**
> I have 2 simple questions:

Does Knoppix use the offical debian repositories, or does it use it's own repositories ? If it uses it's own, how well maintained are they ?

and:

Can Knoppix use Ubuntu packages ? (I am assuming no but I wanted a definite answer.)

1. Knoppix uses the official Debian repositories.

2. Knoppix uses Ubuntu packages. (at least Ubuntu packages are listed in the Synaptic Package Manager)

Also:

I have heard that with the release of the Edgy Eft that Klaus Klopper (Knoppix developer) will be adding Ubuntu to the Knoppix Installer...but this is unconfirmed.

I certainly hope he does because I have yet to  get Ubuntu working on my new computer, but Knoppix detects all my hardware with no problem.

(still using Ubuntu on my older computer, just to clarify)

---

### Post by hermeez on 2006-10-13
Ok I am trying to boot my Ubuntu live cd from a flash drive.
I use an app called flashboot in Winxp to do this. I have used this  app to put Knoppix on a flash drive and it work however I have been   unable to do the same with the ubuntu iso. 

The developer of this software has a states the following

"· a bootable CD-ROM with no emulation boot mode, based on IsoLinux bootloader.
That is useful for most Live Linux CD Distributions and installation disks, for
example, uses this way to boot CD-ROMs.
That's all for now. Please note that support for more no emulation mode bootloaders
(GRUB etc) is planned in the future."

Questions does Knoppix use IsoLinux bootloader and Ubuntu use Grub??

I have a notebook that does not have a cd-rom drive and I want to get XP off it and clean install Ubuntu......Help ](*,)

---

### Post by meng on 2006-10-13
Okay, so you've posted essentially the same topic twice, that's kind of annoying, but since this post has some more details, let me direct you here:
[http://pendrivelinux.com/](http://pendrivelinux.com/)
where there are multiple tutorials on making bootable USB drives from Linux LiveCD distros, using syslinux, not this flashboot thing. There is no specific entry for Ubuntu, but I think the same principle should work.

---

### Post by hermeez on 2006-10-13
Yes, Iposted in the wrong spot initially so I posted again.
Thanks for the link :D

---

### Post by RAV TUX on 2006-10-14
> **hey_ian said:**
> Knoppix is based up on all Debian distro, including packages of SID, Sarge and the upcoming Etch.
In my opinion you should use [Kanotix]("http://www.kanotix.com") if you have any problems detecting your hardware. Kanotix is Debian SID combined with Knoppix technology. Kanotix can be called as a very very advanced version of Knoppix, optimized for HP install. Knopper himself is also always in our #kanotix IRC chat and supports the development of Kanotix. Knoppix is not made for HD install.

I have found Kanotix very disappointing as a hard drive install option,...I prefer and find Knoppix more reliable to install on my hard drive.

Knoppix has never failed me, Kanotix failed to detect basics like my mouse....Knoppix detects everything and just works...

I am not sure what the draw would be to Kanotix? since it doesn't work very well.

---

### Post by RAV TUX on 2006-10-14
> **tturrisi said:**
> Just curious, what hardware doesn't Debian install detect for you?  And are you referring to Sarge, Etch or Sid Debians?  My laptop is a couple yrs old, a P4 3.02, sis chipset, and Etch detects everything and installs fine.  The onboard wifi is not detected by any distro, including Knoppix, so I use pcmcia wlan cards.  I also have other less-than-a-year-old systems & Etch detects all hardware.

specifically "Debian testing amd-64 binary 2"...first off it doesn't have the basic drivers for my CD-rom and ask for floppy loading of drivers...I am sure there is an easy way to fix this but when I test 4 to 5 distros an evening, the distros that can't get the basics down, I have no tolerence for....

There are too many options out there with superior hard drive detection and drivers built in....

Debain and Ubuntu fail to load on my new computer....the reason why they work on your computers is they are old 1 year or older...they fail to be as up to date as Knoppix

but again this is of course subjective and based on isolated variables, specifically my hardware...

If Debian or even Kanotix work for you, then thats great run with it and have fun...

for me they don't but I am glad that Knoppix is here and utilizing the Knoppix Installer I can easily install Debian on my hard drive


I honestly think all Debian deravitives should utilize Knoppix as a base...then overall they would have much more success.

or Knoppix should include more then Debian aand Knoppix as install options,...if Knoppix included Ubuntu (which I hear they will) and Kanotix then this would overcome where these distros fail and overcome the basic obstical preventing these distros from becoming more wide spread...

the first step is either for these distros(Ubuntu, Kanotix, etc)  to unite behind Knoppix or Knoppix to unite them all on the Knoppix Installer.

---

### Post by RAV TUX on 2006-10-14
> **yozef said:**
> I have found Kanotix very disappointing as a hard drive install option,...I prefer and find Knoppix more reliable to install on my hard drive.

Knoppix has never failed me, Kanotix failed to detect basics like my mouse....Knoppix detects everything and just works...

I am not sure what the draw would be to Kanotix? since it doesn't work very well.

OK,...trying Kanotix again.....I got everything working,....I might load Kanotix to my hard drive and try out (again) for a while

---

### Post by hey_ian on 2006-10-15
I do not know how you did try to install Kanotix, but Kanotix is the distro which contains the newest packages and recognizes more modern hardware than any other operating system in use today. 

There is no OS which can beat Kanotix and Knoppix to install to. Even Knopper himself says that Knoppix is only a LiveCD, if you want to install it on HD as a serious Linux, you had better use Kanotix.

---

### Post by mysticrider92 on 2006-11-09
Is doing the Debian install from the Knoppix cd basically the same as downloading and burning the 14 or so cds for Debian, or is it just similar to Debian when you install it?

From the Knoppix site, it looks like this is what it does. I guess I will just try and find out.

---

### Post by RAV TUX on 2006-12-10
>    CHEATCODES AND HINTS FOR KNOPPIX V5.0.1
==============================================================================
                         (last update: 12.05.2006)

These options (can be combined) work from the ISOLINUX bootprompt:

knoppix lang=ch|cn|de|da|es|fr|it   specify language/keyboard
knoppix lang=nl|pl|ru|sk|tr|tw|us   specify language/keyboard
knoppix gmt                         Use GMT-based time
knoppix tz=Europe/Berlin            Use this timezone for TZ
knoppix desktop=fluxbox|gnome|icewm Use specified WM instead of KDE (1)
knoppix desktop=kde|lg3d|larswm     Use specified WM instead of KDE (2)
knoppix desktop=openbox|twm         Use specified WM instead of KDE (3)
knoppix desktop=wmaker|xfce|xfce4   Use specified WM instead of KDE (4)
knoppix screen=1280x1024            Use specified Screen resolution for X
knoppix xvrefresh=60 (or vsync=60)  Use 60 Hz vertical refresh rate for X
knoppix xhrefresh=80 (or hsync=80)  Use 80 kHz horizontal refresh rate for X
knoppix xserver=XFree86|XF86_SVGA   Use specified X-Server
knoppix xmodule=ati|fbdev|i810|mga  Use specified XFree4-Module (1)
knoppix xmodule=nv|radeon|savage|s3 Use specified XFree4-Module (2)
knoppix xmodule=radeon|svga|i810    Use specified XFree4-Module (3)
knoppix 2                           Runlevel 2, Textmode only
knoppix floppyconfig                Run "knoppix.sh" from a floppy
knoppix myconf=/dev/sda1            Run "knoppix.sh" from a partition
knoppix myconf=scan (or config=scan) Try to find "knoppix.sh" automatically
knoppix home=/mnt/sda1/knoppix.img  Mount loopback file as /home/knoppix
knoppix home=scan                   Automatic search for knoppix homedir
knoppix no{apic,agp,apm,audio,ddc}  Skip parts of HW-detection (1)
knoppix no{dhcp,fstab,firewire}     Skip parts of HW-detection (2)
knoppix no{pcmcia,scsi,swap,udev}   Skip parts of HW-detection (3)
knoppix nousb                       Skip parts of HW-detection (4)
knoppix nousb2                      Disable USB 2.x extension
knoppix noideraid                   Disable IDE-Raiddisk detection
knoppix pnpbios=off                 No PnP Bios initialization
knoppix acpi=off                    Disable ACPI Bios completely
knoppix acpi=force                  FORCE ACPI Bios initialization
failsafe                            Boot with (almost) no HW-detection
knoppix pci=irqmask=0x0e98          Try this, if PS/2 mouse doesn't work *)
knoppix pci=bios                    Workaround for bad PCI controllers
knoppix ide2=0x180 nopcmcia         Boot from PCMCIA-CD-Rom (some notebooks)
knoppix mem=128M                    Specify Memory size in MByte
knoppix dma                         Enable DMA accelleration for ALL IDE-Drives
knoppix noeject                     Do NOT eject CD after halt
knoppix noprompt                    Do NOT prompt to remove the CD
knoppix vga=normal                  No-framebuffer mode, but X
knoppix blind                       Start Braille-Terminal (no X)
knoppix brltty=type,port,table      Parameters for Braille device
knoppix wheelmouse                  Enable IMPS/2 protocol for wheelmice
knoppix nowheelmouse                Force plain PS/2 protocol for PS/2-mouse
fb1280x1024                         Use fixed framebuffer graphics (1)
fb1024x768                          Use fixed framebuffer graphics (2)
fb800x600                           Use fixed framebuffer graphics (3)
knoppix keyboard=us xkeyboard=us    Use different keyboard (text/X)
knoppix splash                      Boot with fancy background splashscreen 
                                    + animations + progress bar **)
knoppix toram                       Copy CD to RAM and run from there
knoppix tohd=/dev/hda1              Copy CD to HD partition and run from there
knoppix fromhd                      Skip checking for Knoppix on CD-ROM
knoppix fromhd=/dev/hda1            Boot from previously copied CD-Image
knoppix bootfrom=/dev/hda1          Access Image then boot from previously 
                                    copied CD-Image (enables booting from 
                                    NTFS / ReiserFS) ***)
knoppix bootfrom=/dev/hda1/KNX.iso  Access image, boot from ISO-Image. ***)
knoppix knoppix_dir=KNOPPIX         Directory to search for on the CD. 
knoppix knoppix_name=KNOPPIX        Cloop-File to search for on the CD.
knoppix testcd                      Check CD data integrity and md5sums
expert                              Interactive setup for experts
debug                               Debug boot process

Hint: Using the default DE-bootimage, SYSLINUX boots with german keyboard
layout. The '=' letter is located at Shift-0 on this keyboard (just in
case you want to change keyboard and language with lang=us).

*) Try "knoppix pci=irqmask=0x0e98" if (you have a notebook and) your
PS/2 mouse doesn't work. (Possibly caused by a BIOS-flaw on your board,
BIOS updates can help.) Sometimes, switching to the text console with
Control-Alt-F1 and back to the X-screen with Control-F5 solves the
problem without rebooting, since the X server reinitializes the mouse
driver during that procedure.

**)
You can also have your own splash-screen in putting an executable shell-
script to /cdrom/KNOPPIX/splash.sh. For an example how to do this see:
/usr/bin/splash-knoppix.sh. (Feature added by Fabian Franz.)

***) Bootfrom needs access to a running Knoppix-System with the same Kernel
as the Bootkernel, before it is able to mount the partition / ISO-Image.
This should allow a poor mans install from NTFS-Partitions and makes it
also possible to boot an ISO-Image directly. You can also use wildcards
in the ISO-Filename, but it must be unique. So: If you have just one
KNOPPIX.iso on /dev/hda1 you can access it as: bootfrom=/dev/hda1/K*.iso,
but if there are several, you need to make clear, which one you want.
(Feature added by Fabian Franz.)

If your KNOPPIX CD makes strange noises during boot, or you see
frequent errors like "cloop: read error", or programs on your KDE
desktop keep crashing randomly, then your CD image is probably defective
or incomplete, or your CD-burner created a defective CD due to wrong
writing speed or bad media. This is the most common error reported.
Please boot with "knoppix testcd" to check if the CD is OK, and/or even
better, verify the MD5 checksums that are present on the mirrors before
writing the CD. In some cases, defective IDE controllers cause this
error if you have DMA enabled. Also, please read the KNOPPIX-FAQ.

In case of a failing hardware autodetection, try booting with any of
the "no-" options as shown in the table above, like in
   knoppix noagp noaudio noapm noapic acpi=off nodma nopcmcia noscsi nousb
to skip some critical parts of the autodetection system.

The "noswap" option is useful for a forensic analysis without touching
existing swap partitions.

Some Boards apparently don't pass the proper memory size to the 
linux-kernel. It may cause the message "Panic: cannot mount root file 
system" and the system hangs. Use "knoppix mem=128M" to solve that 
problem if your system has 128MByte memory for example (caution:
you MUST use a capital "M" here).

The "expert" mode provides a very simple interface to loading additional
Kernel modules from floppy disks (ext2 or vfat), plus interactive
configuration of mouse/keyboard/soundcard/xserver. "expert" mode supports
the same boot options as "knoppix".

The "floppyconfig" or "(my)config=/dev/partition" options allow you to
reconfigure the system after autoconfiguration by running a bourne
shell script called "knoppix.sh" from the root directory on the given
device (or floppy). There is a GUI to create such a configuration
floppy disk calles "saveconfig" (also located in the KDE menu under
"KNOPPIX", but experts also know how to do this by creating their own
shellscripts. From Version 2.1 and up, a file called "knoppix.sh", if
located in the toplevel KNOPPIX directory on CD, will also be executed
at startup. This makes ist easier to create customized versions without
having to change anything on the compressed filesystem KNOPPIX/KNOPPIX.

SCSI-Emulation is active for all CD-Roms (unless you switch it off by
using the "atapicd" option), so IDE CD-Writers should work with the
installed versions of cdrecord and cdrdao (or the graphical frontends
thereof, k3b for example).

If your BIOS does not support "no emulation boot" from CD, you can create
two bootable floppy disks by issuing (from Knoppix running on a different
machine) the command "mkbootfloppy", which will create a bootable
Kernel-disk plus a disk containing the initial ramdisk, which will be
prompted for at boottime.

If you wish to remaster the CD, please don't forget to specify
    -no-emul-boot -boot-load-size 4 -boot-info-table \
    -b boot/isolinux/isolinux.bin -c boot/isolinux/boot.cat
as option to mkisofs. Otherwise your CD won't be bootable. The
directory KNOPPIX, containig the compressed filesystem file "KNOPPIX",
must be located in the top level directory of the CD.

Caution: X-Screensaver: Don't start xlock or any screensaver that
requires a password. There are no default passwords on KNOPPIX,
i.e. all accounts are LOCKED unless you explicitly set a password.
See also README_Security.txt about this issue.
If you accidentially hit the screensaver button in KDE,
switch to one of the textconsoles by Control-Alt-F1 and kill
the screensaver (or just set a password for the knoppix user).

If you would like to edit your X-Server configuration manually
(/etc/X11/XF86Config-4 for XFree86 V4.x), use "knoppix 2" to boot
into runlevel 2 (textmode only) and, after changing the X
configuration, start the X environment with "init 5". Note that
you can always leave the graphical environment with "init 2", and
restart it later with "init 5".
;)

---

### Post by gruffy-06 on 2007-02-17
> **Iandefor said:**
> Vista is a Linux-based operating system now ;)?

Not a chance. It is still based on Windows NT.

---

### Post by FuturePilot on 2007-02-20
Is Knoppix meant to be installed? The reason I ask is because I was reading [this]("http://www.knoppix.net/wiki/Hd_Install_HowTo") and came across this> Knoppix is designed & intended to be used as a GNU/Linux ([http://www.gnu.org/gnu/linux-and-gnu.html](http://www.gnu.org/gnu/linux-and-gnu.html)) LiveCD and not a HD installed Linux distro. A HD installed Knoppix will give you a running GNU/Linux ([http://www.gnu.org/gnu/linux-and-gnu.html](http://www.gnu.org/gnu/linux-and-gnu.html)) system but it is not easy to support or administrate and add/remove of software is complicated and is best left to GNU/Linux experts.

I'm thinking about giving it a try on my laptop (I'm on another distro hopping trip again:p ) The only thing that doesn't seem to work is my screen resolution, but I'm sure with the Nvidia driver installed it will be fine. Other than that it's fast and everything else seems to work right. And it supports Beryl too. I love Beryl:p

---

### Post by aysiu on 2007-02-20
It isn't meant to be installed, but it can be installed.

---

### Post by Rodneyck on 2007-02-20
I have read on their forum that some people experience problems when installing on a hard drive, so I chose to give it a pass.

---

### Post by RAV TUX on 2007-02-20
> **FuturePilot said:**
> Is Knoppix meant to be installed? The reason I ask is because I was reading [this]("http://www.knoppix.net/wiki/Hd_Install_HowTo") and came across this

I'm thinking about giving it a try on my laptop (I'm on another distro hopping trip again:p ) The only thing that doesn't seem to work is my screen resolution, but I'm sure with the Nvidia driver installed it will be fine. Other than that it's fast and everything else seems to work right. And it supports Beryl too. I love Beryl:p

> **aysiu said:**
> It isn't meant to be installed, but it can be installed.

> **Rodneyck said:**
> I have read on their forum that some people experience problems when installing on a hard drive, so I chose to give it a pass.

I find the devs stance about KNOPPIX not being meant to be installed is just a system of keeping the peace...with Debian

I had KNOPPIX installed for over 6 months as my primary OS and found it to be the most stable of all Debian distros to install on your harddrive...

I never experienced any problems and in fact found KNOPPIX INSTALLED more stable then Ubuntu....

KNOPPIX installed is Debians best kept secret...

Since I have transitioned from Debian based systems on my primary computers, from Wolvix Hunter, to rPath and now using Sabayon...

I have always returned back to KNOPPIX.....but I would like to install NepaLinux over all other Debian derivatives...

I will probably set up a multi-boot to NepaLinux as my choice Debian derivative.

---

### Post by FuturePilot on 2007-02-21
Ok, I installed it and everything seemed to go fine. Only problem is that X doesn't start automatically. I have to manually start it. And then somehow I wasn't included in the Sudoers file so I couldn't run any root commands:o 
Anyway to fix these things?

---

### Post by RAV TUX on 2007-02-24
> **FuturePilot said:**
> Ok, I installed it and everything seemed to go fine. Only problem is that X doesn't start automatically. I have to manually start it. And then somehow I wasn't included in the Sudoers file so I couldn't run any root commands:o 
Anyway to fix these things?
I do now if you go to your kicker to KNOPPIX to "set root password" you can set that there and should be able to run as root

---

### Post by RAV TUX on 2007-04-28
I just reinstalled the 8GB maxi-DVD of Knoppix....knoppix is pure poetry, art and technology..........

Funny how it is billed as a live Linux system when in reality it is the most stable OS to install on your hard drive, one of the most stable....

and as a friend once noted "if it is not meant to be installed why does it come built with an installer?"

---

### Post by FuturePilot on 2007-05-20
Hmmm. I seem to have misplaced my Knoppix CD#-o I've gone through my Linux collection about 5 times and it's definitely not in there. Oh well, I can use this as an excuse to download the latest version 5.1.1 :lolflag:
Downloading now:popcorn:
Wow! 800KB/s:guitar:

---

### Post by RAV TUX on 2007-05-21
> **FuturePilot said:**
> Hmmm. I seem to have misplaced my Knoppix CD#-o I've gone through my Linux collection about 5 times and it's definitely not in there. Oh well, I can use this as an excuse to download the latest version 5.1.1 :lolflag:
Downloading now:popcorn:
Wow! 800KB/s:guitar:I had trouble with the installer in 5.1.1...so I am glad to have my old 8GB maxi DVD

---

### Post by LaRoza on 2007-05-21
> **RAV TUX said:**
> I just reinstalled the 8GB maxi-DVD of Knoppix....knoppix is pure poetry, art and technology..........

Funny how it is billed as a live Linux system when in reality it is the most stable OS to install on your hard drive, one of the most stable....

and as a friend once noted "if it is not meant to be installed why does it come built with an installer?"

Very true, I use Knoppix on one of my computers, the one with out a hard drive. I boot it from my Flash drive, as per the the instructions at [www.pendrivelinux.com](www.pendrivelinux.com), and use it as my operating system of choice. Even though it is not "installed", it is fast, reliable, and I can carry it around in a six dollar flash drive.

---

### Post by FuturePilot on 2007-05-21
> **RAV TUX said:**
> I had trouble with the installer in 5.1.1...so I am glad to have my old 8GB maxi DVD
Meh, yeah got a bunch of errors. Got it the third time though:-|

---

### Post by 67GTA on 2007-12-01
Does Knoppix still kick butt like it used to? I learned Linux with a Knoppix live cd that has been outdated, and it will not recognize my newest hardware. I still feel nostalgic when it boots up (hugs self) Is it still worth downloading the newest version? Distrowatch hinted in a review that it had slipped over the years, and was kind of buggy.

---

### Post by sneeks on 2008-10-20
there is a video on blip.tv on installing knoppix 5.1 :)

---

