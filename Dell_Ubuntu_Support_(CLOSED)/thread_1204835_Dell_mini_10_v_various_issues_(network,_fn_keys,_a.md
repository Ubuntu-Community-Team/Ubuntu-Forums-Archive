---
title: "Dell mini 10 v various issues (network, fn keys, audio)"
date: 2009-07-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Elvis99 on 2009-07-05
hi everbody,

my gf and I have ordered both a mini 10, hers came with ubuntu and mine with windows. As I wanted to get rid of redmond's product, I also installed ubuntu that came with the other netbook. 
Everything worked out pretty good (I am a complete newb to linux) so basically I am very positively surprised how much power ubuntu packs.
Unfortunately, I also have various issues on both netbooks, that I cannot resolve without your help:

First, the most annoying issue is with the wireless network. I managed to activate the hardware driver (broadcom sta wireless driver) and connected to my wlan which is wep secured. Simulatenously, I wanted to connect my gf's netbook (basically the same config but with a 8gb ssd as hhd) and it couldn't connect. the dialog kept asking for the wep key (it's correct, I checked at least a 100 times). This also has happened to my other (the one that was already connected) netbook, so I assume there is something wrong either with our netbooks or the linux drivers. The most important question: are there any fixes? It's very annoying to have 2 netbooks without wireless capability.

My other problems are just minor issues, for example that the fn keys, which allow control of the speakers, are not working well: I see on the display that I'm putting down the volume (nice graph with speaker and all) but nothing happens.

 The third is mainly an application problem (or at least I think) - when I use skype, during a call, I can't hear what the person is saying but he can hear me just fine, so maybe there is a connection between my fn-keys and the skype sound issue. 

Any help would be appreciated!

---

### Post by Elvis99 on 2009-07-05
Anybody...please? :(

---

### Post by Brandon Williams on 2009-07-07
Unfortunately, the native broadcom driver seems to be flakey with WEP. I have found some WEP wireless networks where it works and some where it where it doesn't. My recommendation for a home network is to switch to WPA, which is significantly better from a security standpoint than WEP. I have not had any problems at all with WPA and the native broadcom driver.

I have not experienced the other issues you mention, and so don't know where to start trying to fix them.

---

### Post by tyroeternal on 2009-07-07
Are you using the default Dell Ubuntu Version, or did you upgrade to the latest Ubuntu release?

Edit:

I found a thread that may give you some help: [http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

Here is the pulseaudio how to fix your problems guide:
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Hopefully between those two you can iron out any issues

---

### Post by Elvis99 on 2009-07-09
> **tyroeternal said:**
> Are you using the default Dell Ubuntu Version, or did you upgrade to the latest Ubuntu release?


Hi, I'm running Ubuntu 8.04.2 (at least it says so after "cat /etc/issue") after getting some updates from Dell (I think).

Thank you for the solutions with the audio issue, I hope that they will work - I'll try them as soon as I can get the very annoying wireless-issues out of the way.

The Network Manager sees none of my wireless networks, and does not save the WEP/WPA keys - please can someone post an idiot-proof, step-by-step guide how to get the wireless up and running. I am a complete newb to Linux, and altough I found some solutions, they mostly include some terminal whacking that I do mostly not understand (in terms of what commands I issue and how I can reverse them if I made a mistake) ..
So please..help me. I am still very impressed by Ubuntu Linux, but this task of fixing network drivers out of the box frustrates me quite a bit!

Thanks,

E.

---

### Post by Talon2 on 2009-07-09
> **Elvis99 said:**
> Hi, I'm running Ubuntu 8.04.2 (at least it says so after "cat /etc/issue") after getting some updates from Dell (I think).



Elvis,

I bought a Mini 9 about 8 months ago.  It came with Ubuntu 8.04 installed.  I had a few issues including fn keys, audio and wifi (hmmm...sounds familiar).  Now my Mini 9 is a pleasure to use and everything works as advertised.  So what did it take for this to happen?

1) BIOS update.  This provided a solution to the lack of f11 and f12 keys.  You should not have this problem.

2) I installed Ubuntu 9.04 Netbook Remix.  I saved all filed I needed to keep on a flash drive and installed clean from a flask drive.

In my opinion 8.04 was simply not ready for netbooks.  9.04 Netbook Remix is ready.

Good luck.

---

### Post by Elvis99 on 2009-07-10
> **Talon2 said:**
> 
In my opinion 8.04 was simply not ready for netbooks.  9.04 Netbook Remix is ready.

Good luck.

Hm okay, I already downloaded the 9.04 release, I'm gonna try it today.

update: I installed 9.04. Runs great on the machine with the 120 gb sata drive. When I tried to install it on the 8 GB SSD machine, the installer says there is not enough space - what now?

[update] okay, managed to install 9.04 on the netbook with the ssd. Loaded updates over cable connection. Restarted. Persistent problem: still cannot connect to wlan network. the other netbook is standing right beside it, and can connect. I'm kinda feeling like tearing my hair out.

---

### Post by Elvis99 on 2009-07-10
When typing in "iwlist scan" i get that none interface (eth0, eth1, lo, pan0) supports scanning. Might there be trouble with the hardware?

edit: I tried updating the BIOS, following these instructions ([http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)) my systemId is, according to getSystemId : "0x02F4" - but I can't find the matching HDR files here ([http://linux.dell.com/repo/firmware/bios-hdrs/](http://linux.dell.com/repo/firmware/bios-hdrs/)).. help? :(

---

### Post by Talon2 on 2009-07-10
> **Elvis99 said:**
> 
update: I installed 9.04. Runs great on the machine with the 120 gb sata drive.


Did you install Ubuntu 9.04 Desktop or Ubuntu 9.04 Netbook Remix?

---

### Post by tyroeternal on 2009-07-10
Okay, this is just a guess, but I had wireless problems that were solved with this method.

1) Install the Aircraft Manager program from this page: [http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html](http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html)
2) Run the program you just installed (it is over in system -> settings? -> aircraft manager)
3) Uncheck both wireless and bluetooth and close the program.
4) Go back in and re-enable both wireless and bluetooth and close it again.

After a few seconds, hopefully your wireless will be working again!

I had this issue with my mini 12, and have heard some mini 9 users say they had it also.  This is a program that dell included in their default install.  It is a shot in the dark, but maybe it will work, it did for me!

---

### Post by Elvis99 on 2009-07-10
> **tyroeternal said:**
> Okay, this is just a guess, but I had wireless problems that were solved with this method.

1) Install the Aircraft Manager program from this page: [http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html](http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html)
2) Run the program you just installed (it is over in system -> settings? -> aircraft manager)
3) Uncheck both wireless and bluetooth and close the program.
4) Go back in and re-enable both wireless and bluetooth and close it again.

After a few seconds, hopefully your wireless will be working again!

I had this issue with my mini 12, and have heard some mini 9 users say they had it also.  This is a program that dell included in their default install.  It is a shot in the dark, but maybe it will work, it did for me!

*expresses his thankfullness in a series of deep bows* It works!! I can't believe it. I have spent more or less the whole day with this damn issue. Thank you so much!

---

### Post by Elvis99 on 2009-07-10
> **Talon2 said:**
> Did you install Ubuntu 9.04 Desktop or Ubuntu 9.04 Netbook Remix?

I accidentally installed the regular desktop version on both machines.  My machine (the one with the 120 gig drive) ran husslefree so I don't know of any reasons to switch to the remix, but if you have some convincing arguments then I'll installl the netbook variant.
Then I installed the remix on the other netbook, but again: no wlan connection. But then, alas, came **ty****roeternal's idea!**

---

### Post by Elvis99 on 2009-07-14
Still haven't resolved the skype sound issue, requesting help.

I ran the commands to kill pulse audio, still when in skype, I'm only recording what sounds like the buzz of the ventilator - (I only hear this when I'm putting front mic boost to maximum in the volume control panel - so I'm kinda recording *something* at least .. )

---

### Post by Elvis99 on 2009-07-17
Still need some working ideas .. :(

---

### Post by patep34 on 2009-07-17
I've got a Dell Mini 9 & I've got the same Skype problem you have - & unfortunately, I haven't found a solution that works for me either. The sound works fine for 15-20 minutes & then I can't hear the other person but they can hear me.

So, I'm searching for a solution in solidarity with you....

---

