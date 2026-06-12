---
title: "Slow Steam Game Download in Ubuntu 18.04"
date: 2019-11-07
forum: Gaming &amp; Leisure
---

### Post by blznguns on 2019-11-07
I recently tried a few distros for comparison (Ubuntu, Solus, Deepin).  I installed Steam and through Steam, attempted to download and install Bioshock Infinite.  I have a 1 GB wired internet.  On Solus and Deepin, Bioshock downloaded and installed in minutes (played very well too).  On Ubuntu, however, download speeds were as slow as 1 KB/s with a peak of 500 KB/s with the game giving an estimated completion timeframe of more than 24 hours.  Why would Ubuntu be so slow compared to the others?  


On a side note, Bioshock is not syncing with Steam Cloud enabled from my previous progress completed on Windows 10.  Does it not work cross-platform?


Thanks!


New Linux User and having a lot of fun with it!

---

### Post by blznguns on 2019-11-09
Yesterday, I tried Steam on Zorin OS 15 and it had the same slow download issue.  So that leaves the score with fast downloads on Windows 10, Deepin, and Solus, with slow downloads on Ubuntu and Zorin.  Since I have openSuse Leap 15.1, Manjaro KDE Plasma 18.1.2, and Linux Mint Cinnamon 19.2 also installed on hard drives, I'll try each of those out as well to see how they fair. 

Again, if anyone has any help here, I was hoping to make Ubuntu my primary OS, but if Steam gaming isn't going to be viable because the downloads for games takes forever, looks like I'll pick another Distro instead or stay with Windows 10.

---

### Post by oldrocker99 on 2019-11-10
I have no idea why one Linux distro would download from Steam quickly, and another would be pokey.

---

### Post by blznguns on 2019-11-10
I should have added that I have 8 OS's across 3 hard drives, so I'm trying these out all on the same computer.  And to update, I tried Mint and Manjaro today and Mint.  Mint was going to take over 24 hours to download Grid Autosport, whereas Manjaro downloaded it in a few minutes.  So the common thread seems to be that if I use Steam on a Ubuntu based distro (Ubuntu, Zorin, Mint) I have the same issue, whereas a non-Ubuntu distro downloads as fast as Windows 10 (Manjaro--Arch, Solus--Independent, Deepin--Debian).  The last distro I have loaded that I can try is openSuse Leap 15.1.  I'm going to guess that it will download just fine since it's not Ubuntu based either.  So there seems to be something related to Ubuntu that is causing the issue.  I might download and try Pop OS to see if a 4th Ubuntu distro has the issue.  I have Elementary OS on a flat panel all-in-one Dell PC that dual boots with Windows 8, so I might try that as well since it is on a different PC.  Might be something about my particular PC that Ubuntu doesn't like.

---

### Post by oldrocker99 on 2019-11-10
I did say goodbye to Canonical and moved to Manjaro, and, well, it's better and faster than a Debian-based system. 

I'm still here, of course, but Manjaro is my permanent distro from now on. It, simply, is Arch made so easy-to-use, so user-friendly and just as suitable for beginners as Ubuntu, that it is, FWIW, high on the DistroWatch page. Its use and justified popularity annoys some Arch users, who are the guys who consider themselves Superior Human Beings for going through the gymnastics of installing Arch itself.

Y'know, the "btw, I use Arch" meme. 

I will always love Ubuntu, which made me a Linux user through and through, but Manjaro is just too good a system.

Anyway, I'm glad you can install Steam games without waiting for hours and hours.

---

### Post by blznguns on 2019-11-10
Well, looks like I solved the problem.  I found this site and instructions - [https://linuxconfig.org/how-to-disable-ipv6-address-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-disable-ipv6-address-on-ubuntu-18-04-bionic-beaver-linux)

It disables ipv6 and once disabled, I launch Steam and start my download and instead of 24+ hours, my download took a few minutes.

---

### Post by blznguns on 2019-11-10
Yeah, I'm really loving Linux and just toying around with it.  I really like something about every Distro I've tried.  I'll have to see which I settle into over time.  I do have to say that so far I really like them all and usually boot into a different one every day.  This weekend I mostly played with KDE Plasma versions of Manjaro and openSuse Leap.  Really liked them both.

---

### Post by oldrocker99 on 2019-11-13
> **blznguns said:**
> Yeah, I'm really loving Linux and just toying around with it.  I really like something about every Distro I've tried.  I'll have to see which I settle into over time.  I do have to say that so far I really like them all and usually boot into a different one every day.  This weekend I mostly played with KDE Plasma versions of Manjaro and openSuse Leap.  Really liked them both.

I had an Amiga back in the 80s. I was about the first person to have one in my area in 1986, and about the last person to still be using one in 1996. I loved AmigaOS, which was inspired at least by UNIX. It was a *fun* computer to use. Another 10 years with Windoze, I got smart and installed Ubuntu 8.04, and have been having *FUN* with Linux ever since. It's fun to use the way the Amiga was.

---

### Post by mastablasta on 2019-11-15
i wonder if this could be my issue. 
CS:GO 
- home and network from local area (same town) - all is quite fluent and no issues. ping still relatively high 80ms (100 mbps optic cable)
- online with other people - lags like hell - ping 150ms-200ms

i know my PC is old but if something works nicely locally with bots, why not with more players? i doubt it is the GPU. old single code CPU could be the issue but it would then be in local game as well. but it's not.

---

### Post by LwIh%*7 on 2019-11-26
If you are having a slow download issue with steam try the following:

In terminal install:

```

sudo apt-get install unbound

```

Then in /etc/NetworkManager/NetworkManager.conf add under the section [main] dns=unbound.

After that rm /etc/resolv.conf then restart Network Manager via sudo service NetworkManager restart after that check /etc/resolv.conf to see if it was re-generated and mentions Network Manager if it does restart the system and then try steam if steam still has a slow download change the download mirror server location from United Kingdom to lets say Germany Dusseldorf that works fast for me on my side and I'm in the United Kingdom. No need to configure unbound it should work out of the box if you follow my instructions.

---

