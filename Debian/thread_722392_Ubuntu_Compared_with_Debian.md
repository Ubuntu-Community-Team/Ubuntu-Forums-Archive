---
title: "Ubuntu Compared with Debian"
date: 2008-03-12
forum: Debian
---

### Post by patrickaupperle on 2008-03-12
How does Debian compare with Ubuntu?
Things like package availability
stability
speed
support
Anything else important

Oh and compare all the aspects with the same version.
Ex one is more stable, but less fast.

**_NOT_** This version of X is faster, this version of X is more stable.

I am hoping for a comparison between sid and 8.04 amongst others

---

### Post by p_quarles on 2008-03-12
Moved to the Debian area.

A site search will turn up several similar threads, by the way.

---

### Post by patrickaupperle on 2008-03-12
Thankyou for the move and sorry for the repeat thread

---

### Post by dptxp on 2008-03-12
When you say Debian, which one ?
1) Debian Stable (currently ETCH)
2) Debian Testing (curently Lenny)
3) Debian Unstable (called sid)

The first one is rock solid, but dated.
Second one is quite stable, like Ubuntu.
Last one is risky, though latest bleeding edge.

Debian is not for absolute beginners.

Best is to install and find out.

---

### Post by patrickaupperle on 2008-03-12
How does debian testing compare with Ubuntu current?
How does Debian Unstable compare with Ubuntu Alpha/beta?

Edit: Which would you suggest?

---

### Post by odiseo77 on 2008-03-12
> **patrickaupperle said:**
> 1) How does debian testing compare with Ubuntu current?
2) How does Debian Unstable compare with Ubuntu Alpha/beta?

3) Edit: Which would you suggest?

1) Pretty much the same versions of the packages, I believe. Although a few days ago I remember having seen a more recent version of some packages in Debian Lenny (testing), so probably Debian Lenny has more recent versions of the packages. If you want the be fully up-to-date on Debian, you must dist-upgrade your system regularly with the slight risk it implies (it's always good to read the messages apt-get gives you when attempting to dist-upgrade)

As for stability, I'd say Debian Lenny is more stable than Ubuntu 7.10. 

As for usability, Ubuntu is one of the easiest distros I've tried; once you have all the necessary repositories enabled you can set up almost everything with just a few clicks here and there. I wouldn't say Debian Lenny is hard, but you probably will have to use the command line a bit more often instead of just clicking, but if you're used to dpkg/apt-get/synaptic, it shouldn't be a problem. 

Hardware support: IMO, Ubuntu has more hardware support out of the box.

2) I haven't used Debian Unstable or Ubuntu Alpha, so I can't give you an opinion (sorry).

3) I'd suggest Debian Testing: it's stable enough yet up-to-date and definitely has something that hooks you up (at least in my case)... I don't know, I just find it more versatile than Ubuntu (but this is my very personal opinion).
EDIT: I'd suggest whatever suits you better; if you want usability, then go for Ubuntu.

Greetings

---

### Post by jrusso2 on 2008-03-12
Debian is much more stable then Ubuntu and its faster.  The only thing better about using Ubuntu is the ease of use.  Debian is not nearly as easy to setup as Ubuntu

---

### Post by dptxp on 2008-03-13
If you want Debian stable with good hardware detection, use Kanotix.

If you want Debian unstable (bleeding edge) in stable mode, try sidux. sidux is pretty fast, and installs in say 7 minutes.

You can always try these Live (slow in live mode)

And if you are interested in Debian Testing, wait for Ubuntu Hardy.

---

### Post by notwen on 2008-03-13
I share my opinions running Debian stable for personal use and server use for the past 4-5 years.  I made Ubuntu my personal use OS around Edgy's release.  That said I still use Debian, currently Etch for my server.

stability
---
Debian stable has to be one of the most, if not the most thorough distros, they are very strict about what gets into their repos.  Using this for personal use may limit your choices.  

speed
---
Personally I believe Debian is a little faster than your vanilla Ubuntu install.  Generally because they do not include numerous user-friendly applications in a basic install.  So your system isn't as bloated.

support
---
Debian forums are active, not quite so much as Ubuntu's.  Their mailing list is very active about updates/fixes/etc.

---

### Post by patrickaupperle on 2008-03-13
Thankyou everyone. Debian sounds good. I will probably be dual booting soon. Anyone know a good backup app? (you have to backup before modifying partition tables.)

---

### Post by souneedalink on 2008-03-13
Debian has mp3 support in the default install!

Debian is what you make of it but if all you want is a nice default install they have that too.

backup - burn a dvd

package availability - couldn't be better
stability - there is nothing more stable than debians stable release
speed - do a custom install and only install/start what you need and I doubt you will find much that boots faster
support - ? debian docs, forums, mailing lists, howtos, irc, ....

---

### Post by cdiem on 2008-03-14
At patricaupperle: If you have 512 (better have 1024 MB) RAM and 10GB (better 20GB) free hard disk space, you could try Virtualbox and emulation of debian and ubuntu - and thus you will find which one better suits your needs, which one is better, faster, etc. Even in emulated environment, Debian with KDE and using 256MB RAM is blazing fast for me, in comparison to k/x/ubuntu. But you will the answer for yourself. The best thing about Virtualbox is that you don't need to repartitioon your hard drive; the emulated distros are handled like a one big file of for instance 10 GB (or whatever size you gave it), and uninstallation is just as easy as deleting the .vdi file. I myself have been playing with Virtualbox recently a lot, and feel sorry that I haven't used it earlier.

---

### Post by patrickaupperle on 2008-03-14
> **cdiem said:**
> At patricaupperle: If you have 512 (better have 1024 MB) RAM and 10GB (better 20GB) free hard disk space, you could try Virtualbox and emulation of debian and ubuntu - and thus you will find which one better suits your needs, which one is better, faster, etc. Even in emulated environment, Debian with KDE and using 256MB RAM is blazing fast for me, in comparison to k/x/ubuntu. But you will the answer for yourself. The best thing about Virtualbox is that you don't need to repartitioon your hard drive; the emulated distros are handled like a one big file of for instance 10 GB (or whatever size you gave it), and uninstallation is just as easy as deleting the .vdi file. I myself have been playing with Virtualbox recently a lot, and feel sorry that I haven't used it earlier.

Which method of downloading and installing should I use? ex. jigdo or net inst or whatever

---

### Post by cdiem on 2008-03-14
Well, I installed it in Virtualbox just from the first CD - the one that has written CD1-kde on it; it could as well have been CD1-xfce for a xfce desktop ot just CD1 for a gnome desktop; this will give you a complete, quite configured desktop - and a very fast one, actually. If you feel a bit more like a master, you could try a netinstall, which would work ok in virtualbox as well, thus giving you a base system, which you could build the way you like. As for downloading method - I used the good old http one, but any other should work fine.

---

### Post by patrickaupperle on 2008-03-14
What about the install dvd?

---

### Post by odiseo77 on 2008-03-14
> **patrickaupperle said:**
> What about the install dvd?

With the install dvd, you will need to download the whole dvd iso image (obvious) which probably contains lots of stuff you don't need. If you have a wired internet connection, I'd suggest the netinstall cd; you just boot it, select your packages set and they're downloaded from the internet while installing.

---

### Post by patrickaupperle on 2008-03-14
Will net install give me all the same stuff? (in the installation) IF so, can you point me to a good guide for net install of debian testing?

---

### Post by souneedalink on 2008-03-14
I suggest CD1 as it contains the packages needed for a nice default desktop install.

---

### Post by patrickaupperle on 2008-03-14
I am already downloading the DVD. I want either DVD or net install. Which is better? Do I end up with the same system? Daily or weekly build? Why would CD be suggested? Is DVD bloated or something, or is it just file size?


Edit: Never mind, the entire downloaded so far DVD just got deleted. I am going cd. but I still want to know the answers to my other questions. (for future reference, like when/if I install  to my hard drive)

---

### Post by souneedalink on 2008-03-14
The majority of the desktop task is contained on CD1. The DVD contains a lot of stuff you probably wont ever install much less use.

Net install is okay if you dont mind downloading a lot. Net install of testing/sid is cool because testing/sid changes a lot. No point in having a obsolete system at install when you can pull the latest in at install time. Net install of stable is kind of pointless IMO since it doesn't change much and CD1 today is just as good as CD1 in three months.

---

### Post by patrickaupperle on 2008-03-15
After 9 hours of downloading and installing, last night I finally got Debian Lenny installed in Virtual box. It seems extremely similar to ubuntu.

---

### Post by kerry_s on 2008-03-15
> **patrickaupperle said:**
> After 9 hours of downloading and installing, last night I finally got Debian Lenny installed in Virtual box. It seems extremely similar to ubuntu.

9 hours?
slow connection?

[http://people.debian.org/~joeyh/d-i/images/daily/netboot/mini.iso](http://people.debian.org/~joeyh/d-i/images/daily/netboot/mini.iso)

6.8mb 10->30 minutes to download

the rest of the time could have been installing already. 

i use the etch net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

32mb can install both etch and lenny, for lenny expert mode is used.

---

### Post by patrickaupperle on 2008-03-15
First I downloaded cd #1 which took 2 hours. Then after that during the install process it decided to download 700 something files. that took 4 hours. it also took at least 2 hours for the installation before and after the 4 hour download. That is 8 hours there. The last hour could have come from my inability to choose packages or maybe some of the other downloads took longer. All I know besides what I have said is that I started before lunch and finally finished after 9 pm.

---

