---
title: "Will ubuntu run on this machine?"
date: 2006-05-15
forum: Desktop Environments
---

### Post by zenlunatic on 2006-05-15
I have a Dell Inspiron 3500 which I think is 266mhz p2 but it might be faster.  I'm going to bump the ram up to 192mb.  It has cdrom.  Is their like an ubuntu-lite which I should use instead.  Otherwise I think I'm going to use damn small linux, debian, or slackware.

---

### Post by aysiu on 2006-05-15
Try Xubuntu.

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by Ramses de Norre on 2006-05-15
Do you have any linux experience yet? If so go for a very lightweight window manager like fluxbox, icewm, blackbox .. (using fluxbox myself, it rocks!)

If you don't: try out xubuntu first untill you're comfortable enough with the linux way of doing things.

---

### Post by zenlunatic on 2006-05-15
Yeah I have some experience but I don't like messing with stuff too much which is why I ran ubuntu on my other laptop but I am selling that for the money.

---

### Post by zenlunatic on 2006-05-16
Okay I can confirm its a p2 366mhz with 256mb ram.  Will dapper run on it good?

---

### Post by aysiu on 2006-05-16
[QUOTE=zenlunatic]Okay I can confirm its a p2 366mhz with 256mb ram.  Will dapper run on it good?[/QUOTE] Xubuntu will run just fine on that.

---

### Post by aggiechemist on 2006-05-16
I have the same laptop. For starters, the processor is actually a Celeron at about 300 MHz. I run it at about 128 MB RAM.

Xubuntu is a very good bet. I don't use it myself however, because I had gigantic headaches trying to get wireless networking going.

I currently use Breezy on it. It is kinda slow, but it still does OK for just my websurfing and email. I don't do any of my real work on it. 

As for wireless, I use a PCMICIA card. I find that it only works if I boot with the card out and then I plug it back in after booting. It then autodetects and sets it up. It won't do that if the card is in when  I boot. I have no idea why that is.

Xubuntu might work with the same plug/unplug, but I never tried it. My Xubuntu disk didn't even come with wireless support to begin with, so that is something a newbie might not want to dive right into adding.

Dapper should be OK too. I haven't migrated this system yet, but I think it will do just fine.

Note that sound is not gonna work. The sound has never worked on any linux distro I have tried, EVER. You're welcome to try, but smarter nerds than I have tried and failed.

Hope this helps. Stick Breezy on it, and I think you will be happy if you just have a little patience.

---

### Post by zenlunatic on 2006-05-16
So when you follow the directions for the xubuntu install and do a server install, it doesn't load wireless drivers?

Sound doesn't even work in dapper?

---

### Post by pillu on 2006-05-16
I am running ubuntu on my dell inspiron 7000 laptop (P2 192 MB RAM). It installed fine and detected the wireless networking and also the sound card. No hassle at all. Just that gnome was too slow on it, so i installed the Xubuntu desktop on it with

**sudo apt-get install xubuntu-desktop** 

It is working fine now. Xfce is much faster than gnome and is the way to go on older system. I would recommend you to install the normal ubuntu system first just to get all the hardware working right and then install xubuntu desktop later.

---

### Post by aggiechemist on 2006-05-16
Maybe it's my ignorance, but I'm not sure what a "server install" refers to. It just didn't include the wireless package (I think the apt-get package name is wireless-tools). I think it might have been left out in Xubuntu's striving to keep things small and simple, so I would be understanding if that were true.

I got the tools on another computer and had to port them over and do dpkg to install them. Wireless still didn't work at that point, but that might have been the plug/unplug thing.

Also, that attempt was with the Dapper beta version of Xubuntu, not a stable version.

And sound has not worked in Warty, Hoary, Breezy, or Dapper. Tried 'em all.

---

### Post by joeybunda on 2006-05-16
I am sucsessfully running UBUNTU 5.10 on two AMD 500mhz machines w/128 mb ram... Needless to say - ubuntu runs slow on this setup - but it works without any crashes.

---

### Post by joehayhurst on 2006-05-16
I am running the latest Dapper on an old Compaq Armada E500 which I reckon must be about 5 or 6 years old. I think its a Pentium II 450Mhz or something like that. It has 196MB RAM and it works great.

In fact I'd go so far as to say it runs a least as quick as my work laptop which is a 
Centrino 1.7Ghz (I think) with 768MB with Windows 2000.

The only thing is that it seems to be a bit slow at loading applications, the hard disk chugs away noisily, but I think that is the age of the machine as much as anything else. If I had a bit of spare cash I might bung a tad more memory in it but it doesn't really need it, to be honest.

This is the first computer I got up and running Linux with. I started on Breezy 5.10 and it installed at the 2nd time of asking, not problems at all. Funnily enough, Dapper took 2 gos at installing too, but I didn't have to make any changes, it just worked 2nd time round.

The sound works perfectly, the network card took no configuring, EVERYTHING just works! The only thing I have any problems with are codecs which I have mainly been able to get around eventually -- especially thanks to  [Easy Ubutu]("http://easyubuntu.freecontrib.org/") and [Automatix.]("http://www.ubuntuforums.org/showthread.php?t=138405") 

Ubuntu restored my faith in Linux. When I installed Dapper, for some reason I expected it to be slower as it was a newer version -- I was wrong, obviously still stuck in Windows-land.

I would recommend you should definitely install Linux (Ubuntu or any other distro you can get to work) on any hardware that is struggling to run Windows. It will save you having to throw good hardware away, which is money in the long run.

And if Ubuntu users would like a laugh, why not not see Microsoft's own hardware recommendations [Microsoft's own hardware recommendations]("http://www.microsoft.com/technet/windowsvista/evaluate/hardware/vistahardware.mspx") for Vista. Bear in mind that in my experience, XP is completely unusable with less than 512MB as it is, but they recommend 'at least 64MB'!

---

### Post by uhu_maotouying on 2006-05-24
IBM Thinkpad 600x 2645-xxxx (500 MHz P3 & 300 MB) running Hoary & Breezy

KDE is always far to slow and even Gnome is sometimes unbearable on that particular machines. However xfce 4.22 is quick, stable and really fun, I hope the xfce team will not blow it up.

---

### Post by M_Hamada on 2008-03-13
For older machines, try Fluxbuntu:  [http://www.fluxbuntu.org/](http://www.fluxbuntu.org/)

---

### Post by mister_p_1998 on 2008-03-14
Try the Puppy Live CD, it runs wifi out of the box, and runs great on old hardware, I run it on a PII 500 and a PIII 800, its as fast as my 1.6ghz vaio!
Steve

---

