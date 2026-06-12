---
title: "Feisty on Dell Inspiron 1420 problems"
date: 2007-08-07
forum: Dell  Ubuntu Support
---

### Post by weird_c00kie on 2007-08-07
[SIZE="3"][COLOR="Red"]***** EDIT *****
I worked out how to fix the problem.
Scroll down to the 11th post ( [http://ubuntuforums.org/showpost.php?p=3160037&postcount=11](http://ubuntuforums.org/showpost.php?p=3160037&postcount=11) ) for more info :)[/COLOR][/SIZE]


I got my brand new Dell Inspiron 1420 delivered this morning and i picked it up full of excitement, ready to install Ubuntu on it, when i ran into an error before the live cd even booted up.

the CD loads up to the bit where it gives you the 4-5 options of starting the live cd, checking the disk for errors and all that
when i choose to run the OS, it starts loading, but then goes into a full-screen console thingy and says:


> BusyBox v1.1.3 (Debian  1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

(initramfs)

and then lets me type stuff, but i don't know what i'm meant to type

can anyone help?


initially i thought i'd gotten the wrong version of ubuntu (i tried the 32bit one initially), so then i tried the 64bit one that i used to install Ubuntu on my desktop and it comes up with the same thing.
can anyone shed some light on what's going on?

has microsoft finally found a way of permanently infecting my computers with windows and preventing me from using something better, or is it something entirely different?


ANY help will be VERY welcome. i eagerly look forward to feedback. ideally i'll have the laptop fully up and running before my uni lecture tomorrow so i can go back to typing up my notes instead of having to handwrite them

---

### Post by iggykoopa on 2007-08-07
I would recommend following the directions in this post [http://ubuntuforums.org/showthread.php?t=509408](http://ubuntuforums.org/showthread.php?t=509408) there are a couple drivers you need that you can't get from the normal install disk.

---

### Post by chiten on 2007-08-07
[SIZE="3"]HI!! i have the same problem...i have my new inspiron 1420 since last week and i couldn´t install ubuntu 7.04 yet...somebody told me that using a 64bits distro is better than a 32bits, is that true? i think that this howto will work with the same steps but using 64bits packages...am i wrong??([/SIZE]..thanks!!

---

### Post by weird_c00kie on 2007-08-07
hey iggy, thanks for the response

i saw that thread before i posted mine... i thought there might be an easier way. most of the subsequent posts explaining how to overcome certain problems go right over my head :(

i guess that i just have to pray that once the alternate cd download finishes and i try it it works straight away, because i know that if i try to go into all that stuff i'm going to get very lost and very frustrated :p

---

### Post by weird_c00kie on 2007-08-07
oh, and to add further evidence to my n00bness, i couldn't even work out if the intel core 2 duo the laptop comes with is a 64bit one or not. i'm downloading the 32bit version of the cd just to be on the safe side

---

### Post by Syke on 2007-08-08
All Core 2 Duos support both 32 and 64 bit Ubuntu.

---

### Post by kuja on 2007-08-08
If you were just going to install ubuntu on it anyway why didn't you get the 1420N w/ubuntu  instead? ... would have been easier (and more compatible) no?

---

### Post by ticklecricket on 2007-08-08
> **chiten said:**
> [SIZE="3"]HI!! i have the same problem...i have my new inspiron 1420 since last week and i couldn´t install ubuntu 7.04 yet...somebody told me that using a 64bits distro is better than a 32bits, is that true? i think that this howto will work with the same steps but using 64bits packages...am i wrong??([/SIZE]..thanks!!

Yes, that will work. I was up till 4 am last night doing so!

---

### Post by weird_c00kie on 2007-08-08
> **kuja said:**
> If you were just going to install ubuntu on it anyway why didn't you get the 1420N w/ubuntu  instead? ... would have been easier (and more compatible) no?

because both Dell and System76, in all their infinite wisdom, don't ship the ubuntu laptops to australia. Believe me, I tried :p
I emailed System76 about it and called Dell, but neither one has plans of offering those systems in Australia any time soon. So I did the next best thing, which was to match the specs of the 1420N to those of the 1420 that I got. Maybe I can beg Dell for an Ubuntu recovery disk? would that work?

I have to wait until tomorrow morning now to download the PCLinuxOS live CD so it don't use up anymore of my peak-time download allowance on linux distros. I already downloaded umm... 3 today :/

I think I'm going to stick to the 32bit version though... the 64bit one has only ever given me trouble on my desktop system.

---

### Post by weird_c00kie on 2007-08-09
FINALLY! 


using the bits and pieces of useful information from this thread
[http://ubuntuforums.org/showthread.php?t=509408](http://ubuntuforums.org/showthread.php?t=509408)

i managed to get it working :D
X works, wireless works, it all works :D

3 cheers for ubuntu and another wave goodbye to windows! mwahaha

---

### Post by weird_c00kie on 2007-08-09
I thought I'd list where I got all the files I installed from, just in case anyone needs to know... or in case I need them again.

As I said, I followed specker's guide, which is here:
[http://ubuntuforums.org/showthread.php?t=509408](http://ubuntuforums.org/showthread.php?t=509408)

the xserver-xorg-video-intel_2.1.0-1ubuntu1_i386.deb file he listed didn't work for me, so i had to find it elsewhere. after leap-frogging through threads here, i found this post [http://ubuntuforums.org/showpost.php?p=3084952&postcount=75](http://ubuntuforums.org/showpost.php?p=3084952&postcount=75) which contained these two links:
[http://people.ubuntu.com/~kyle/crestline-i810/xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb](http://people.ubuntu.com/~kyle/crestline-i810/xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb)
[http://people.ubuntu.com/~kyle/915resolution_0.5.3-0ubuntu1_i386.deb](http://people.ubuntu.com/~kyle/915resolution_0.5.3-0ubuntu1_i386.deb)

As far as the CD images are concerned, i downloaded ubuntu's Alternate CD from:
[ftp://ftp.iinet.net.au/linux/ubuntu-cd-images/7.04](ftp://ftp.iinet.net.au/linux/ubuntu-cd-images/7.04)

and the PCLinuxOS image from one of the mirrors here:
[http://www.pclinuxos.com/index.php?option=com_ionfiles&Itemid=28](http://www.pclinuxos.com/index.php?option=com_ionfiles&Itemid=28)

it's the PCLinuxOS that really saved me
Since the wireless works straight away with it, i was able to download the files i needed and easily create the extra partition for them. Then I just booted into ubuntu and installed the files after X crashed

i feel so good now! :D

[COLOR="Red"][SIZE="3"]***** EDIT *****[/SIZE][/COLOR]
I forgot to mention this page:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages)
Even though the modem fix is the only one with a link, you can find the others just by entering the full filename into google :)

---

### Post by aeo24 on 2007-08-09
I have the same specs with a nvidia card and cant get my wired ehternet card recognized. I tried to rmmod the tg3 driver and then dkms add tg3 mod with no results mind giving me a step by step guide how you got it working?

---

### Post by weird_c00kie on 2007-08-23
> **aeo24 said:**
> I have the same specs with a nvidia card and cant get my wired ehternet card recognized. I tried to rmmod the tg3 driver and then dkms add tg3 mod with no results mind giving me a step by step guide how you got it working?

To be honest, I don't know if it *is* working... Because I got the wireless working, I never really tested the wired connection. I remember trying it once, but I don't think it worked, so I focused on getting the wireless working. And then once the wireless was working, I forgot all about the wired one :tongue:

---

### Post by MrSootentai on 2007-08-23
Hey wierd_c00kie
what wireless drivers are you using? I have a broadcom on my 1420 and using the 1420n Fresh Fiesty guide didn't help. I still couldn't get it working.
Could you help me out a bit??

---

### Post by sebald on 2007-08-24
I fussed around with the Feisty alternate and got nowhere, then the Feisty DVD got me only a bad x-server start and just a command line. 

So I took the advice of another topic and, as far as I'm concerned skipping right to Gutsy Tribe 5 is the way to go - I used the kubuntu version, alternate installer, and it found the wired and wireless network drivers immediately, went right to 1440x900 screen display, etc. It does offer the nvidia driver in a separate control panel, but enabling that screwed eveyrthing up and I had to reinstall. (I have the nvidia card installed...) Initially no 'net on konqueror, but it would ping in the terminal, but after installing Firefox (not installed initially, go figure) all was well.

Trouble is, grub didn't find Windows Vista's partition, but I'm now going to put in a manual edit on my grub boot.lst file and see if that doesn't fix it. Cross your fingers...

---

### Post by sebald on 2007-08-24
> **sebald said:**
> 
Trouble is, grub didn't find Windows Vista's partition, but I'm now going to put in a manual edit on my grub boot.lst file and see if that doesn't fix it. Cross your fingers...

And with the little edit of the menu.lst file (not /boot.lst, sorry) in /boot/grub, all was well. We'll see what sort of fun trouble we get into using alpha versions of the next release :-) but it initially seems fine on wired and wireless connections.

---

### Post by kuja on 2007-08-24
> **MrSootentai said:**
> Hey wierd_c00kie
what wireless drivers are you using? I have a broadcom on my 1420 and using the 1420n Fresh Fiesty guide didn't help. I still couldn't get it working.
Could you help me out a bit??
Of course it didn't, they're two different systems with rather different components. The 1420n's have Intel 3945ABG Wireless.

---

### Post by MrSootentai on 2007-08-24
Tired of all of this none sense I just downloaded Gusty Tribe 5 beta and...
IT ALL WORKS!!!!
Now I just have to fix sound, and may sure wireless truly works.
But so far Ubuntu already detected my card and all it's settings now it is just looking for the windows driver.

---

### Post by weird_c00kie on 2007-08-29
> **kuja said:**
> Of course it didn't, they're two different systems with rather different components. The 1420n's have Intel 3945ABG Wireless.

Actually, one of the reasons I got the 1420 in Australia is because it had the same components as the 1420n in the US. Because I wanted to have as few problems as possible, I made sure to check that all the components were the same, since Dell doesn't ship the 1420n with Ubuntu pre-installed to Australia.

But, since MrSootentai has managed to get things running in Gutsy, I guess I don't have to worry too much about this now :)

My laptop is still working more or less perfectly.
I did try running Beryl on it, but after an initial successful run, I was punished with horrible blank white screens, no matter what settings or rendering engines I tried. Disappointed and truly disheartened, I was forced to remove Beryl and just use the 'Desktop Effects' thing that comes with Ubuntu.
I have a feeling that Beryl's ugly crash had something to do with me not having money for the nVidia card and sticking to the default Intel one :-k :rolleyes:

---

### Post by kybishop on 2007-09-01
that's awesome that the gutsy alt cd works

should I use the 64 bit gutsy or the 32 bit gutsy cd?

---

### Post by Yoke &amp; Chung on 2007-09-20
Hi,

I am facing similar problem on my Dell Inspiron 1420, however, my spec is different from the 1420n, I got a GeForce 8400M graphics adapter instead, will the installation work for me as well?

Thanks in advance

---

### Post by notwen on 2007-09-20
To get your CD recognized try [this]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/CD_media_not_recognized").  I would then recommend using the new remastered [Dell Ubuntu CD iso]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Dell_Remastered_Ubuntu_7.04_ISO") to save yourself form having to correct some of the bugs which have been fixed for the 1420 and 1420n models.  Hope this helps. =]

---

### Post by weird_c00kie on 2007-10-10
> **notwen said:**
> To get your CD recognized try [this]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/CD_media_not_recognized").  I would then recommend using the new remastered [Dell Ubuntu CD iso]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Dell_Remastered_Ubuntu_7.04_ISO") to save yourself form having to correct some of the bugs which have been fixed for the 1420 and 1420n models.  Hope this helps. =]

sweet! thanks for that! i bookmarked the site for next time i might need to reinstall on my laptop :D

---

