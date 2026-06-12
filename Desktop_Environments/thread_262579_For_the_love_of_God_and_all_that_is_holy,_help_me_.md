---
title: "For the love of God and all that is holy, help me set up ubuntu as a WAP"
date: 2006-09-21
forum: Desktop Environments
---

### Post by cabe on 2006-09-21
I will get right to the point!

I would like to use my laptop (equipped with an Atheros based WG511T wireless card) as a wireless access point, so I read this guide and followed it to the letter:
[http://www.linux.com/article.pl?sid=06/07/10/1729226](http://www.linux.com/article.pl?sid=06/07/10/1729226)
However, hostapd never starts and always spits out "Starting advanced IEEE 802.11 management: hostapd...failed."

I used to have Debian Sarge.  I followed the above guide to the letter with the same result.  With Debian, I had to install hostapd from the backports repository.  I thought that could be my problem, so I switched distros (to ubuntu).  I still have the problem!

I have looked up every scrap of information regarding hostapd or using linux as a WAP till blue in the face.  Some of what I've read:
[http://hostap.epitest.fi/hostapd/](http://hostap.epitest.fi/hostapd/)
[http://www.devicescape.com/docs/uwp/package_guide/pkg_hostapd.php](http://www.devicescape.com/docs/uwp/package_guide/pkg_hostapd.php)
[http://lists.shmoo.com/pipermail/hostap/2006-March/012812.html](http://lists.shmoo.com/pipermail/hostap/2006-March/012812.html)
[http://lists.shmoo.com/pipermail/hostap/2002-December/000732.html](http://lists.shmoo.com/pipermail/hostap/2002-December/000732.html)
[http://mobile.newsforge.com/article.pl?sid=03/10/24/2234235&tid=102&tid=95&tid=2&tid=14&tid=31](http://mobile.newsforge.com/article.pl?sid=03/10/24/2234235&tid=102&tid=95&tid=2&tid=14&tid=31)
[http://wiki.personaltelco.net/index.cgi/LinuxAccessPoint](http://wiki.personaltelco.net/index.cgi/LinuxAccessPoint)
[http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html](http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html)
I have applied all relevant information from those links with zero progress, both attempting to make a WAP with hostapd and also without hostapd.

Back when I had Debian and was dealing with this, I posted on several linux related forums.  I was shocked to get absolutly no response, given the amount of exposure my question had gotten.
[http://www.devhardware.com/forums/networking-34/hostapd-problem-help-with-using-linux-as-wap-102754.html](http://www.devhardware.com/forums/networking-34/hostapd-problem-help-with-using-linux-as-wap-102754.html)
[http://www.linuxhelp.net/forums/index.php?showtopic=8220&hl=](http://www.linuxhelp.net/forums/index.php?showtopic=8220&hl=)
[http://www.wirelessforums.org/network-troubleshooting/help-using-linux-laptop-access-point-6604.html](http://www.wirelessforums.org/network-troubleshooting/help-using-linux-laptop-access-point-6604.html)
[http://www.techsupportforum.com/showthread.php?t=114317](http://www.techsupportforum.com/showthread.php?t=114317)
[http://www.linuxforums.org/forum/linux-networking/69434-hostapd-wont-start-no-matter-what.html?highlight=cabe](http://www.linuxforums.org/forum/linux-networking/69434-hostapd-wont-start-no-matter-what.html?highlight=cabe)
[http://www.linuxquestions.org/questions/showthread.php?t=478211&highlight=cabe](http://www.linuxquestions.org/questions/showthread.php?t=478211&highlight=cabe)
[http://forums.debian.net/viewtopic.php?t=8480&highlight=](http://forums.debian.net/viewtopic.php?t=8480&highlight=)
[http://www.linux-on-laptops.com/forum/showthread.php?t=489&highlight=cabe](http://www.linux-on-laptops.com/forum/showthread.php?t=489&highlight=cabe)
[http://www.linuxforum.com/forums/index.php/topic,179825.0.html](http://www.linuxforum.com/forums/index.php/topic,179825.0.html)

At this point, I don't care if I set up the access point with hostapd or not.  I don't even care about encryption anymore.  I just want the damn thing to work!

So please, for the love of God and all that is holy, help me!!!!!

---

### Post by cabe on 2006-09-22
C'mon guys! I've dropped to the 3rd page now and noone has anything to say?

---

### Post by peabody on 2006-09-22
I have no experience with hostapd, so I can only offer general suggestions.  I take it you're trying to launch hostapd from /etc/init.d/?  Try launching it manually from the command line and see what error messages it gives you.  Also, I would look to see if hostapd keeps logs, and if so, check them out for any error messages.

---

### Post by moufranica on 2006-09-22
> **cabe said:**
> 
So please, for the love of God and all that is holy, help me!!!!!

I do not know if what I am going to say would be considered a flame? But I have no such intentions. I am only curious. That is, I curious why after spending so much time on various forums and reading so much that you have not thought of getting a cheap AP? 

I do not know if buying a dedicated AP from cheap sources like newegg and tigerdirect is an option for you, but that does sound good. There are people who promote the use of old 486 systems to run as gateways using Linux. I am of the idea that in this day and age it is more practical to get a simple cheap router (unless your needs are quite complexe and in that case one would know better what to do). 

All these said, I do apologize as I have no idea at all how to setup linux as an AP, but can point you in another direction if that is what you want. And that direction is the world of VMWare appliances. I believe there should be quite a few such appliance made (and some part of me think that the gurus who made the guide for setting up Linux as AP might also want to make such an appliance so that other mere mortals like us can benefit from it and they would ofcourse will benefit by having to answer less quetions).

Please do consider posting your query on VMWare forums regarding their appliance challenge (it's over) and other similar threads. Perhaps the key word appliance and AP might hit the right note and perhaps you will have more success that way? Just a thought.

---

### Post by cabe on 2006-09-22
I didn't take it as a flame at all! :)

There are several reasons for me not getting a cheap AP.  I've had bad experiences with cheap wireless routers and I want to be able to more fully configure my WAP/router, but the biggest reason is that I'm a poor college student who's stuck with using what he's already got! (My dad's old laptop with a burnt out screen and his old wireless card)

Anyway, I did end up getting this thing to work without hostapd.  However, the network seems to be stuck in B mode! :(  Anyone have an idea of how to get this thing working in G or even mixed mode?  I've looked up the iwconfig commands and the only one that looks like it applies is the rate command.  I've tried iwconfig ath0 rate 54M, but it doesn't work!  Any ideas about this?

---

