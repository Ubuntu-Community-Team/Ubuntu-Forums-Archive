---
title: "Dell Studio Ubuntu Install Guide"
date: 2010-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by matt.cohenprice on 2010-06-27
**UPDATE:** I recently upgraded my system to 64-bit Ubuntu Studio 10.10. Ditched the proprietary ATI driver for the open-source default Radeon driver, made sure to enable KMS (see [this page]("https://help.ubuntu.com/community/RadeonDriver")), and multiple monitors work essentially hot-plug-and-play, which is wonderful. Sound worked on install, as did skype with my built-in webcam and mic. So, some of what still follows still applies, but I have been able to solve many of my 10.04 problems in 10.10 without a problem. I am not planning on re-writing the entire how-to, but if you have a similar system and have a question, I'll do my best to answer it!

---------------


Hello!

Welcome to my Dell Studio Ubuntu 10.04 guide! I just bought a Dell Studio 1458 with the goal of installing Ubuntu 10.04 alongside Windows 7. I ran into more trouble than I expected, but after a marathon week staring at my computer screen, and lots and lots of forum posters around the web, was able to fix most of it. I documented my travels, and am publishing them here. **The goal? **To help those who are considering buying a Dell Studio for Ubuntu,and to help those who have with installing and setting up a 10.04 dual boot on a new Dell Studio. 

This post will address issues from 32 vs 64 bit systems, partitioning, hibernation and suspend issues, grub, a total lack of sound any sound at all, and a few other nitpicky things I have picked up over the years. Enjoy!

[COLOR="BLUE"]**Table of Contents:**[/COLOR]
[LIST=1]
[*]Who am I?
[*]What machine am I using, and how did it work out of the box?
[*]32-bit vs. 64-bit
[*]Dell Dual-Boot nightmare
[*]Partitioning your dual-boot install
[*]Getting your Dell Studio to produce sound
[*]Dual monitors, emerald, and compiz
[*]Other applications and tweaks I've picked up along the way
[*]Problems still to solve
[/LIST]
[COLOR="BLUE"][B]
1. Who am I?[/B]
[/COLOR]I am a four-year vet of Ubuntu, in the category, I would assume, of &#8220;average Ubuntu user.&#8221; I know my way around terminal and synaptic and can troubleshoot some problems myself but often rely on the technical expertise of others online to get me through problems. So, not a noob, but no expert either. The solutions present here are not my own but those of others I have scavenged from around the web. I will try to link all of them to their original source. This is my first how-to of any sort on these forums.

[COLOR="BLUE"]**2. What is the machine? How did it work out of the box?**
[/COLOR]In May, 2010, I customized and bought a Dell Studio 1458 from the Dell website. The one hardware downside I have experienced thus far is that the notebook top and the keyboard loooove my fingerprints. Otherwise, my general feel of the computer hardware is great &#8211; its a sturdy machine, the optional backlit keyboard is great,  and the screen is beautiful. Here's what I am working with:

Dell Studio 1458 base
Intel Core i5-520M 2.40GHz processor
4GB DDR3 RAM
Back-lit keyboard (works great!)
14&#8221; 720p display w/ webcam and built-in mic (which worked in Skype instantly!)
ATI Mobility Radeon HD 4530 Graphics Card w/ 512 MB RAM
500GB SATA Hadr Drive
Slot-load DVD-R
Intel WiFi Link 6200 G+N
Dell Wireless 365 Bluetooth (haven't tested it yet with an actual device, but Ubuntu seems to recognize it just fine)
[COLOR="BLUE"]
**3. 32-bit vs 64-bit?**[/COLOR]
I read as much as I could comparing 32-bit to 64-bit versions of 10.04 , including [this]("http://ubuntuforums.org/showthread.php?t=502754&page=2"), [this]("https://help.ubuntu.com/community/32bit_and_64bit"), and [this]("http://ubuntu-tutorials.com/2007/11/26/32bit-vs-64bit-ubuntu-that-is-the-question/"). After my research, and appreciating my want to have the best of the best, I decided to go with 64-bit. I installed it, and within a day decided to wipe and start over with 32-bit. I identified no major failures, just lots of little things (as everyone else says, it is unstable). Sometimes the wifi would turn off and not turn back on unless I rebooted in Windows and re-enabled it. Sometimes the battery icon would disappear from the notification area. Little things like that. Sometimes sleep and hibernate would work, but usually not. 32-bit is great &#8211; it is running more smoothly and all the icons stay where they are supposed to be. It even hibernates and suspends w/o problem - something my last Linux box (a 2005-era Toshiba laptop) never did. When I upgrade to Meerkat ([10.10]("http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#Releases")) maybe I will try again, especially now that I have all these other fixes figured out. 
**My recommendation: stick with 32-bit for now.**
[COLOR="BLUE"][B]
4. The Dell Dual-boot nightmare[/B]
[/COLOR]
If you already have a recent Dell laptop and have tried to install Windows 7 and Linux alongside, you already know that it royally screws up. You can install Ubuntu and Grub and boot into Ubuntu as many times as you would like. Then, you can boot into Windows 7 once. After that, nothing works &#8211; Grub never shows up. Other people have reported a pre-grub error that looks like "Grub loading... XXXXXX symbol not found." My error looked different, but the same fix still worked

Error:
```
PXE-E61: Media test failure. Check Cable Now.
PXE-M0F: Exiting Broadcom PXE ROM.
Operating System not found. 
```

Apparently, a program that comes installed on Windows 7, Dell Datasafe Local Backup, doesn't like Grub very much. When you boot into Windows, DDSLB corrupts the Grub bootloader, and you will no longer be able to boot from any OS on your hard drive until you repair Grub.

**If you have not yet installed Ubuntu**, then the solution is simple. In Windows, use DDSLB to burn your two initial backup DVDs &#8211; this is the closest thing you will get to a Windows 7 disk, in case you ever need to reinstall Windows. Once you do this, DDSLB can be uninstalled without a problem &#8211; it becomes a pretty useless program, especially if you spend most of your time in linux.  Also, the web-world (and common sense) tells me that the program doesn't have anything to do with actual recovery if your windows system does need to be repaired &#8211; you can do everything you need to do from the disks you use DDSLB to burn. So... 
[LIST=1]
[*]take your computer out of the box
[*]install Windows
[*]make your backup disks
[*]uninstall DDSLB (I also uninstalled Dell Datasafe Online Backup) from the Windows 7 Control Panel &#8211; Add/Remove programs)
[*]Then install Linux and Grub
[/LIST]
**If you have already installed Ubuntu, booted Windows, and discovered this bug the hard way**, the solution is a bit more complicated. Thanks to merry_meerkat for writing a [how-to to fix the problem]("http://ubuntuforums.org/showthread.php?t=1447786"). Here's what you do:
[LIST=1]
[*]Boot from your Ubuntu LiveCD
[*]Reinstall Grub (there is a wonderful tutorial [here]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2"); I, like, merry_meerkat, found that only the third method [chroot] worked for me)
[*]boot into Windows
[*]uninstall DDSLB and DDSOB
[*]Boot from your Ubuntu LiveCD again
[*]Reinstall Grub again (step 3 corrupted your boot sequence all over again)
[/LIST]After doing this, I was able to boot easily into Windows 7 and Ubuntu 10.04.

[B][COLOR="BLUE"]5. Partitioning your Dual-boot Install
[/COLOR][/B]
My Dell Studio came with three partitions on it: a 40mb fat16 partition labeled &#8220;DellUtility,&#8221; a 15gb partition labeled &#8220;RECOVERY&#8221; (from which it appears Windows 7 actually boots from), and a 455gb primary Windows partition (the C: drive). 

In the past, when setting up dual-boot with Windows XP (which operated off of one partition), I simply used the custom partition setting in the LiveCD install wizard to create four partitions: Windows (NTFS), a shared data partition which I mounted in Ubuntu as /home (ext3), a smaller root partition (ext3), and a swap partition equal to the size of my built-in RAM. [Here's a screenshot of that system's partition table]("http://www.box.net/shared/s1msvjmr2p").

With three Windows partitions now instead of one, partitioning gets a bit more complicated. Hard drives can only have four primary partitions, and I needed six. To get around this, I embedded all my linux partitions (/, /home, and swap) in an extended partition. The Ubuntu install wizard partitioner can't do this so well. I found it significantly easier to boot into Ubuntu using the LiveCD and set up my partitions in gparted, the wonderful Ubuntu partition software, then run the install wizard. If you are looking to do something similar, here are basic instructions. 
[LIST=1]
[*]In Windows, defragment your C: drive. This moves all the files on the drive to the far 'left' of the partition, making it easier to shrink the partition later. If you are doing this right out of the box, C: is probably not very fragmented, but its good practice anyway.
[*]Launch Ubuntu from your 10.04 liveCD
[*]Open GParted (System &#8594; Administration &#8594; Gparted)
[*]Use Gparted to shrink your Windows partition (probably sda3), leaving unallocated space on the right. I shrunk mine to 55 gb, as I do run the full Office 2007 suite and Adobe CS4, so I need the space.
[*]In the unallocated space, create an extended partition that utilizes the entire rest of the drive. 
[*]Within the extended partition, create, from the right side:
[INDENT][LIST]
[*]a swap partition equal to your built in RAM (for me, 4gb)
[*]a root partition where Ubuntu operating system files will be stored (ext4; I made mine 25 gb but could have made it much smaller, probably 15 or 20)
[*]a home partition where your Ubuntu documents and settings files will be stored (ext3 or ext4; allow this to fill the rest of the unallocated space on the drive). *A note about your home partition filesystem: in dual-boot scenarios, this is the partition you may want access to in both Ubuntu and Windows. I formatted my home partition as ext3 so that I could open it from Windows. While there are indeed some [major advantages of ext4]("http://en.wikipedia.org/wiki/Ext4") over the older filesystems, keeping ext3 allowed me to install and use [ext2fsd]("http://www.ext2fsd.com/") to read and write to my home partition from Windows. If this is confusing to you, check out this great [Primer on Filesystems]("http://www.linuxjournal.com/article/9449").*[/LIST][/INDENT]
[*]Apply changes. [My 500GB hard drive looks like this]("http://www.box.net/shared/knygk92brz").
[*]Install Ubuntu from LiveCD
[*]When you are asked to choose a partition scheme, select &#8220;specify partitions manually (advanced)&#8221;
[*]Select the 15-25 gb partition we called the &#8220;root&#8221; partition above. Make its mount point &#8220;/&#8221; (the root of your system). Check the box to format the partition.
[*]Select the large partition in the middle of the drive we referred to as your &#8220;home&#8221; partition above. Make its mount point &#8220;/home&#8221; and check the box to format the partition.
[*]Complete installation.
[/LIST]
[COLOR="BLUE"][B]6. Getting your Dell Studio to play sound (speakers and/or headphones)
[/B][/COLOR]
This was one of the biggest hurdles of my install. I read many posts (including [here]("http://ubuntuforums.org/showthread.php?t=1298668"), [here]("http://www.namanb.com/2009/07/ubuntu-sound-problems-on-dell-studio.html"), [here]("http://superuser.com/questions/65135/ubuntu-9-10-x64-has-no-sound-while-ubuntu-9-04-32-bit-does"), [here]("http://superuser.com/questions/65135/ubuntu-9-10-x64-has-no-sound-while-ubuntu-9-04-32-bit-does"), [here]("http://ubuntuforums.org/showthread.php?t=969611&page=3"), [here]("http://ubuntuforums.org/showthread.php?t=1140667&page=2"), and [here]("http://ubuntuforums.org/showthread.php?t=997506")) and tried many of their solutions. What finally solved it was a wonderful tutorial about upgrading Alsa, Ubuntu's underlying &#8220;Sound Architecture&#8221; program. Using **[ALPHO2K's guidance]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")**, I upgraded Alsa from 1.0.21, the version that ships with Ubuntu 10.04, to 1.0.23. I did get one error message in that install while upgrading alsa-utils, but I found a solution to that [here]("http://trac.64studio.com/64studio/ticket/511") -- if alsa-utils configure or make fails, just run those four sudo commands and try again.

Before this success, I had downloaded and installed PulseAudio. I recommend doing this, even if you don't sound trouble or if the above fix works for you. From terminal:
```
sudo apt-get install padevchooser paman paprefs pavucontrol pavumeter pulseaudio-module-zeroconf 
```
The full PulseAudio Device Chooser and Volume Control GUIs will help you get a sense of where any sound issues you have are occurring.

EDIT: After this solution, I ran into additional another major hurdle: pulseaudio and flash were fighting over control of ALSA, so sound mixing between programs did not work. If the first sound I played came from skype and rhythmbox, which use pulseaudio, no flash sound (pandora, youtube,etc) would work. If the first sound I played was flash, no sound through pulse would work. After much troubleshooting, I found that the failure was a lack of the document that channeled ALSA-using applications like flash through pulseaudio, so PA could mix all the sound together. I followed the directions of post #3 [here]("http://ubuntuforums.org/showthread.php?t=1412153"), and it worked like a charm. Now, alsa-apps are being forwarded to pulse, and everything mixes well together.
[COLOR="BLUE"][B]
7. Dual monitor and desktop effects[/B][/COLOR]
For my ATI Radeon Graphics Card, I installed the FGLRX proprietary driver from ATI to get full functionality. Installing is easy &#8211; a little symbol may pop up in your notification area telling you it is there to install. If not, find it under System &#8594; Administration &#8594; Hardware Drivers. There is an [open source version]("https://help.ubuntu.com/community/RadeonDriver") of the driver as well, which I have not experimented with yet. 

Possibly the best part about the ATI graphics card and driver is that, for the first time since I have used Ubuntu, I can use dual monitors just like I used to in Windows, and switch back and forth between one and two monitors (when my laptop is on my desk vs when it isn't). Using the Display Manger in the administrative ATI Catalyst Control Center, I selected "multi-display desktop with..." (not "single display desktop [multi-desktop]"), and then was easily able to correct resolution information for my two monitors. 

If I turn my computer on with the external LCD attached, it opens with both displays. If I turn my computer on without it attached, I only get one display - as close to perfect as I need, for now.

Once I knew this was working, I installed compiz and emerald. A great howto is [here]("http://www.hackourlives.com/install-compiz-fusion-and-emerald-in-ubuntu-10-04-lucid-lynx/"). 

Next goal: change xorg.conf files (what controls how many desktops I have) without restarting the computer!

[COLOR="BLUE"][B]
8. Other software and tweaks[/B][/COLOR]

Here are a few additional tweaks most of those not new to Ubuntu will already know:
[LIST=1]
[*]activate the canonical partner repository (system &#8594; administration &#8594; software sources &#8594; other software &#8594; check the &#8220;[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner&#8221; line). This gets you many great applications not in the standard repo. 
[*]activate the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository. This repo helps you play Windows- and Mac-type Audio and Video files, protected DVDs, etc etc. From terminal:```
 sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update 
```
[*]Update your software sources. From terminal:```
sudo apt-get update
```
[*]Via apt-get install in terminal, the Synaptic Package Manager, or the Ubuntu Software Center, you can then install the following:[/LIST]
[INDENT][LIST=1]
[*]acroread &#8211; Adobe Acrobat 9, which I like far better than the Ubuntu built-in PDF viewer
[*]acroread-fonts &#8211; allows acroread to display fonts correctly
[*]ubuntu-restricted-extras &#8211; MP3 support, java, flash, DVD playing, etc
[*]libdvdcss2 &#8211; encoded DVD playing
[*]w32codecs (or w64codecs if you installed 64-bit OS) &#8211; more video codecs, such as DivX and Quicktime
[*]Skype (which worked on my Dell Studio with no audio customization at all, a huge improvement from the Toshiba I used to run Ubuntu on!)
[*]Gimp (it's not photoshop, but for the basic stuff I'd rather not boot into Windows 7)
[*]Graphical Disk Map (from Software Center; easy way to intuitively figure out what is hogging all your hard drive space)
[/LIST][/INDENT]

**[COLOR="BLUE"]9. Problems still to solve[/COLOR]**
Some issues are still on my to-do list. If you have solutions or similar problems, please post here. If you are looking for solutions. check back regularly - hopefully I'll solve them soon!
[LIST=1]
[*]Screensaver/password: I like to have my computer password protected if I leave it idle, so I checked box in the screensaver dialogue to require a password on wake up. From Suspend or Auto-screen-off, it works fine. But if the screensaver has been enabled (for me, after 2 minutes) but the screen hasn't turned off yet (5 minutes), moving the mouse will simply freeze the screensaver, not show me a box asking for my password. However, the box is there! I can type my password in blind and hit 'enter', and the screensaver leaves and I'm back. Weird.
[*]Quiet GRUB boot that hides the grub menu even though I have two OSs -- apparently this setting has been disabled in GRUB2.
[/LIST]

---

### Post by merry_meerkat on 2010-07-29
Nice and very helpful writeup!
As you know I have a similar machine (Dell Studio 1747) and yes, sound was a headache again when I installed Lucid (no headphone sound). However, it turned out I didn't have to do much at all to solve my sound problems. Unlike what you describe above, I just added the following line to **/etc/modprobe.d/alsa-base.conf**
```
options snd-hda-intel model=dell-m6
```

See also: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("No sound would play through headphones. Solved by adding the following line to /etc/modprobe.d/alsa-base.conf options snd-hda-intel model=dell-m6  https://help.ubuntu.com/community/HdaIntelSoundHowto")

...just posting this in case it helps someone.

---

### Post by ptn107 on 2010-07-30
I have a new studio 1749.  Ubuntu 10.04 x64 worked right out.  All I had to do was enable my wireless in the Hardware Drivers applet and add 'wl' to /etc/modules.

---

### Post by matt.cohenprice on 2010-08-05
Good to know that other people are having success too.

merry_meerkat, (or others!) a quick question re sound: in the last two kernal updates, my hard-fought battle for sound turned south. When I boot in 2.6.32-24.39 (updated today) or 2.6.32.24.25 (updated July 27), I get no sound! But when I boot into the older 2.6.32.23.24, it works fine. Pulseaudio volume manager shows everything going to the right place, but nothing comes out.

Any suggestions?
I'm not opposed to removing Pulse and trying something else, its just aggravating that it works in the older kernal but not the upgrade!

Thanks!

---

### Post by merry_meerkat on 2010-08-06
Hi,
as I outlined in my post, all I did after installing Lucid was to add that one line to alsa-base.conf. I changed nothing else and have no problem since.

About my kernel:
```
uname -r
```
...says that my kernel is **2.6.32-24-generic**, and it's working fine.


I have no idea if it helps, but this is what I would try in your situation (obviously totally based on my own experience, and taken from [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")):

1. Find your sound card model:
```
cat /proc/asound/card0/codec#* | grep Codec
```

2. Find the entry in this list that most closely resembles your sound card:
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt")

3. Add the following line to **/etc/modprobe.d/alsa-base.conf**
```
options snd-hda-intel model=XXXX
```
...replace XXXX with the entry you found under point 2.

---

### Post by ptn107 on 2010-08-07
I was told installing linux-backports-modules-alsa-lucid-generic also fixes it?

---

### Post by Tejus on 2010-08-29
Thanks for the guide! I have ordered a Studio 1558, this should come in very handy once i get it.

One clarification though. I had once been playing around with gparted, and ended up formatting my whole hard drive by mistake! So you recommend that we create rescue disks using DDSLB. Can I use these rescue disks to get back all the default partitions and my windows installation, even if i accidentally format the whole 500 GB Drive again?

---

### Post by rbx0122 on 2010-08-29
> **Tejus said:**
> Thanks for the guide! I have ordered a Studio 1558, this should come in very handy once i get it.

One clarification though. I had once been playing around with gparted, and ended up formatting my whole hard drive by mistake! So you recommend that we create rescue disks using DDSLB. Can I use these rescue disks to get back all the default partitions and my windows installation, even if i accidentally format the whole 500 GB Drive again?
  
I am not so sure the rescue disks will recreate the partitions. You may have to do this manually.

---

### Post by Tejus on 2010-08-29
Oh...yeah...well, i mean as long as i can recover my installation of windows after wiping the entire drive.

Because Dell doesn't ship the installation discs with the laptop :-/ . That is one useful disc, especially when linux is involved. I have had to reinstall atleast 10 times when I was experimenting with ubuntu, grub, xbmc, etc :)

---

### Post by matt.cohenprice on 2010-08-29
Tejus, I have not yet had to reinstall Windows 7, so I havent used the recovery discs yet. It is likely that the recovery discs will revert the entire hard drive to its shipping defaults, ie delete your ubuntu partitions. So, after recovery, you may have to start over and reinstall linux -- I am not sure.

merry_meerkat, re sound issues, as soon as I get a minute I have a few more questions for you - I still cant get sound to work in the newest kernel.

---

### Post by ecabacis on 2011-01-19
Hi Matt,

Very nice topic you have there.

Btw, i am a total newbie in using Linux but i really want to learn it and i think the best way to learn it is to use it on a day-to-day basis for me to totally explore it.

My platform is Dell Studio XPS 1340, can i run Ubuntu on it?

I have tried dual booting W7 and xUbuntu on it but FAIL.:oops: Maybe because i am not familiar on how to do it or my platform is not really compatible for Linux, that i doubt. :)

The main issues i have with my laptop is after installing xUbuntu, my wireless didn't work, i also tried plugging it to LAN but i still cannot acquire any IP so there is no update for me.

I am from Singapore, so i do hub a USB modem for internet from Starhub but the installation files inside the USB modem are .exe, therefore i am unable to install the modem for me to be able to use it.

Can you help me on installing Ubuntu on my lappy? Any points:KS or tips:KS will do for sure especially if it will come from you.

There are lots of things to learn in Linux, bit by bit i know i can learn it and be a linux user. (Been a windows user since childhood)

Should i use Ubuntu or xUbuntu? :)

Looking forward to your reply.

Regards,

Edmon

---

### Post by matt.cohenprice on 2011-01-20
Ecabacis,

Welcome to Linux! It wasn't long ago people were saying that to me on these forums...

A Dell Studio XPS 1340, eh? You mean something new, like [this one]("http://www.dell.com/us/business/p/xps-14/pd")? If so, unless you have a specific reason to use xubuntu, I'd stick with the regular distro ("Ubuntu"). Xubuntu will lower your graphics functionality substantially, for no good reason if you are using a recent machine.  

You should have no problem installing Ubuntu (any distro you want) onto a Dell--they tend to work pretty well. What specific problems are you having with Dual Boot? All the basic steps I outlined in my original post still apply: 
[LIST=1]
[*]make backup disks using Dell Datasafe Local Backup 
[*]uninstall DDLB
[*]defrag your HD from windows
[*]boot from your Ubuntu Live CD
[*]use Gparted to add partitions to your HD (at least root/swap partitions, or home/root/swap partitions [as common online], or files/root/swap, as I do.)
[*]reboot, install Ubuntu from CD (in partitioning section, choose custom, and make sure Ubuntu knows to mount the partitions you created correctly)
[/LIST]

Regarding your internet issue...can you post some additional info? Are you trying to use the USB modem directly plugged into your laptop, or are you using WLAN/LAN? If you are using the modem directly, I can't be of much help, but I am sure you are not the only user on these forums trying to get in via a Starhub modem in Singapore--hopefully someone has written a driver/programmed  workaround for linux. If you are having issues with LAN/WLAN, I can only give you basic troubleshooting hints. You'll have to get help from someone more advanced on the forums.

Good luck!!

---

### Post by matt.cohenprice on 2011-01-20
All, 

Has anyone solved suspend and hibernate issues for a Dell Studio? I haven't figured out how to get my system (Ubuntu Studio 10.10 64-bit) to recover from hibernate or suspend, although it seems to enter either state without a hitch....

Thanks!

---

### Post by ecabacis on 2011-01-20
Hi Matt,

Thanks again for the reply.

My system is the one on this pic.

[http://laptopspc.files.wordpress.com/2010/03/dell_studio_1340-laptop2.jpg]("http://laptopspc.files.wordpress.com/2010/03/dell_studio_1340-laptop2.jpg")

If xUbuntu is not a good choice, i will go and download the Ubuntu for netbook.

ubuntu-10.10-netbook-i386 --> this is the correct one for my device right?

What happened to me after installing xUbuntu is i am unable to get any ip address either through LAN or Wifi. Seems like drivers for my NIC and Wifi is not configured.

Will try to dual boot again Win7/Ubuntu and ill let y'all know if its a success this time.

Thanks again! Hope to become and Ubuntu geek someday.. :)

---

### Post by matt.cohenprice on 2011-01-20
> **ecabacis said:**
> If xUbuntu is not a good choice, i will go and download the Ubuntu for netbook.

ubuntu-10.10-netbook-i386 --> this is the correct one for my device right

Ecabacis, If I were you I'd install the Desktop version, not the Netbook version--Netbook Edition is designed for the small screens of Netbooks (6" to 10") and uses a different interface...one that I have never used.

The Desktop version isn't called "Desktop" because it's not for Laptops--It's called "Desktop" because it isn't for servers. The Desktop Edition is the most commonly supported on these forums and should work just fine on your 13" laptop.

---

### Post by matt.cohenprice on 2011-01-20
> **ecabacis said:**
> If xUbuntu is not a good choice, i will go and download the Ubuntu for netbook.

ubuntu-10.10-netbook-i386 --> this is the correct one for my device right

Ecabacis, If I were you I'd install the Desktop version, not the Netbook version--Netbook Edition is designed for the small screens of Netbooks (6" to 10") and uses a different interface...one that I have never used.

The Desktop version isn't called "Desktop" because it's not for Laptops--It's called "Desktop" because it isn't for servers. The Desktop Edition is the most commonly supported on these forums and should work just fine on your 13" laptop.

---

### Post by ecabacis on 2011-02-01
Hi Matt.. I have successfuly installed Ubuntu 10.10 desktop edition and i am very well pleased with the UI.. The only problem i am facing now is my sound.. It not working!! Tried to folloe ur solution on your post but unfortunately it is still not working.. Can help me solve my problem.. Just let me know what details do i need to capture in order for u to check it.. I have tried re-installing ALSA but no luck at all.. Please help.. Ow another thing.. How can i access my ext3 in W7? I am not seeing it..

---

### Post by matt.cohenprice on 2011-02-01
Let's do the easy one first: 

> **ecabacis said:**
>  Ow another thing.. How can i access my ext3 in W7? I am not seeing it..

There are various tools for 'teaching' windows 7 to access ext3 partitions. You can see a rundown of the common ones [here]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/"). I am 99% positive that I am using [ext2fsd]("http://sourceforge.net/projects/ext2fsd/") and that it works just fine with Windows 7, but I'm on my Linux side as usual so I can't confirm. If you have trouble with the install let me know and I'll confirm which freeware I'm using.


> **ecabacis said:**
> The only problem i am facing now is my sound.. It not working!! Tried to folloe ur solution on your post but unfortunately it is still not working.. Can help me solve my problem.. Just let me know what details do i need to capture in order for u to check it.. I have tried re-installing ALSA but no luck at all...

No sound at all, eh? This is the identical problem I faced when running 10.04. My solutions were never complete--for a long time, I could only get sound to work in one, older kernal. I'm not sure what to tell you. If you tried the ALSA upgrade already, the best I can tell you is to look carefully through the pulseaudio menus and tools--for example, play some music and check the pulseaudio volume control tool: does pulseaudio think music is playing, but you hear no sound? That is going to be a different issue than if pulseaudio shows nothing. Make sure to try flash-based sound (ie Pandora or a youtube video) as well as non-flash sound (ie rhythmbox, VLC, etc). 

I am not a Linux expert by any means, but if I had to guess I'd say the sound issue seems to be a kernal issue with these particular dell models--so when I fixed my sound in 10.04, I fixed it (maybe inadvertently) only in the kernal that was at the time the most current. You may want to try [Ubuntu Studio 10.10]("http://ubuntustudio.org/"), which uses a different kernal that handles sound in a [whole different way]("https://help.ubuntu.com/community/UbuntuStudio"). Although I don't do serious enough sound editing to really put the realtime kernal to use, it did seem to solve my sound issues...

Good luck.

---

### Post by dismalvoyage on 2011-02-03
I was wondering if anyone else has had touchpad issues with the Studio series? I found that for the most part, everything has worked surprisingly well in my 1558 Core i5 model, but it seems as if each individual has different issues. I recently installed Maverick, my first real solid attempt at installing a non-virtualized Linux distro. The touchpad had been extremely sensitive, but it more or less worked the way it was supposed to. Earlier tonight in class I had booted my Win7 partition briefly to check on some of my virtualized distros, and after rebooting into Maverick, the touchpad had become even more sensitive. I made the mistake of recklessly seeking a solution (damn PCC coffee) and ended up trying this...

[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html)

Since then the touchpad has been much less sensitive, but I have completely lost my ability to vertically scroll and I cannot for the life of me figure out why. Deleting the files didn't work. Following other scripting tutorials didn't work. Uninstalling and reinstalling any touchpad-related packages wouldn't change anything either. It's like it just went in there and broke something. If anyone else has experienced similar issues, or have any insight as to what might be going on here, I'd love to talk. I really don't want to have to drag an external mouse around all day when I know there is a perfectly good touchpad sitting there. It was working just fine days before. :confused:

<EDIT: Nevermind, I reinstalled Maverick using a non-Dell tweaked copy, in a safe and orderly manner, and now almost everything works perfectly. Everything except some touchpad issues after booting back into Win7. This seems to be remedied by reinstalling synaptics-dkms_1.1.1_all.deb. Dell Studio 1558 Core i5, 32-bit Maverick. Peace.>

---

