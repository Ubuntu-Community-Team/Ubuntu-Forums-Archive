---
title: "New to Ubuntu need some tips"
date: 2009-04-03
forum: General Help
---

### Post by portdizzal on 2009-04-03
I have a Dell 8100 with a Pentium 4 and I have gotten tired of Windows updates screwing my computer and making it run slow.

I have installed Ubuntu 8.10 and it is now my only running OS on my pc. I have a few questions a bout things so that i can get it setup as simple as possible and not have to run a bunch of crap that i dont need.

1. After the initial installation what do I need to do to get everything turned on that needs to be turned on.

2. I have a ATI Radeon 9200 pro video card that i am having trouble getting a correct way of getting the driver for it and being able to make changes with ATI catalyst control center. every method i tried that i found left the computer starting in low graphics mode. I now have a fresh start Ubuntu and have done nothing to it.

3. I have a 5.1 surround sound system with my PC and sound only comes through 1 speaker.

4. I play City Of Heroes and I would like to know what is the best program to be able to run it at its best. from what i understand is Wine would be the best for that.

I appreciate any help i can get. And please, keep it simple. I understand alot of you like to do your whole code writing and take the hardest possible path but i have no desire to be doing all that crazy stuff. So the more simple it is the less chances of me screwing anything up.

---

### Post by Tobi-fp on 2009-04-03
For the ati and wireless if you have so, go to system->administration-hardware drivers and enable them alle, very simple :)

For the wine thing do:
alt+F2
write: gnome-terminal
in terminal write:
sudo apt-get install wine

now you can install city of heroes

if you want to listen to mp3's and such just do a google search for it, many guides how to..
Any ways, ubuntu is trying to make everything as simple as possible (and in so many ways ubuntu is easier than windows for a fact), but there are still some things that you yourself may have to work hard for..

Hope you are ready for the challenge ;)

---

### Post by philinux on 2009-04-03
Answer for 2.

Click the medibuntu link below and follow instructions. Also install ubuntu-restricted-extras from synaptic.

---

### Post by coffeecat on 2009-04-03
Go to System > Adminstration > Synaptic Package Manager. Look for the package 'ubuntu-restricted-extras'. Select it for installation and click on apply and, so long as your internet connection is configured, it will download and install for you. Restricted extras gives you a load of stuff that for licensing reasons can't be included in the installer: flash plug in, proprietary codecs, java, MS core fonts, and so on.

Now go to [http://www.medibuntu.org/](http://www.medibuntu.org/) . Go to the repository howto and enable the medibuntu repository. Now you will be able to install libdvdcss2 (for playback of commercial DVDs) and VLC (an excellent multimedia player).

---

### Post by tr33m4n on 2009-04-03
I don't mean to sound patronising, but have you installed all the latest updates at all?

If you go to System > Administration > Software Sources, and make sure that under the 'Ubuntu Software' tab, Proprietary drivers for devices is checked... and under the 'Update' tab check Proposed updates and Unsupported updates is checked. Clicking close will now download the extra repository information.

The in System > Administration > Update Manager, install the updates shown (if none are showing your computer is up to date... however I usually click 'Check' just to make sure)

In terms of your graphics, I would suggest having a look at Hardware Drivers (Restricted Drivers) under Administration and see if it finds any for your graphics card (as Tobi-fp suggested :)).

---

### Post by coffeecat on 2009-04-03
> **tr33m4n said:**
>  and under the 'Update' tab check Proposed updates and Unsupported updates is checked. Clicking close will now download the extra repository information.

**BAD** idea. [-X :wink:

See [this thread]("http://ubuntuforums.org/showthread.php?t=899262"). Also: [https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates) .

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.

Proposed updates is for experienced users to check for bugs. Telling a newcomer to use the proposed repo is giving them unnecessary grief.

---

### Post by portdizzal on 2009-04-03
Quote:
Originally Posted by tr33m4n  
and under the 'Update' tab check Proposed updates and Unsupported updates is checked. Clicking close will now download the extra repository information. 

BAD idea.  


thanks for the heads up. im sure there is most everything i will need already in the Ubuntu OS so I just wanted to know how to make it work best for my computer. So please be careful what you tell me to install and what not. Also I agree VLC is one of the best media players out there. I had it on my windows and never had a video it wouldnt play.

---

### Post by coffeecat on 2009-04-03
> **portdizzal said:**
> im sure there is most everything i will need already in the Ubuntu OS

**Except** proprietary codecs, flash player, etc, etc. Do install ubuntu-restricted-extras as philinux and I suggested. It won't break your system. Promise. :p

By the way, if you want to quote another post, just click the - er - quote button at the bottom right of the post you want to quote. It looks better. :wink: And to the right of it is a multi-quote button so that you can quote more than one post.

---

### Post by portdizzal on 2009-04-03
> **coffeecat said:**
> **Except** proprietary codecs, flash player, etc, etc. Do install ubuntu-restricted-extras as philinux and I suggested. It won't break your system. Promise. :p

By the way, if you want to quote another post, just click the - er - quote button at the bottom right of the post you want to quote. It looks better. :wink: And to the right of it is a multi-quote button so that you can quote more than one post.


yeah i already clicked post reply before realizing i should have quoted. I am at work so i only have a short amount of time to reply to this at the time. appreciate all the help though. Ill look into all of this deeper. the video card controls are my top priority.

---

### Post by portdizzal on 2009-04-05
> **Tobi-fp said:**
> For the ati and wireless if you have so, go to system->administration-hardware drivers and enable them alle, very simple F)

Ok I tried this and no drivers came up at all. The box is completely empty all the way through. Its almost as if ubuntu is not seeing any of my hardware.

---

### Post by markbuntu on 2009-04-05
The 9200 is no longer supported by the proprietary ati drivers but the open source ati or radeon or radeonhd driver is fully functional for that card. There are a zillion threads around here about that.

To get your sound working go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

You can look in the Multimedia and Video forum for more help with sound and video.

---

### Post by portdizzal on 2009-04-05
> **markbuntu said:**
> The 9200 is no longer supported by the proprietary ati drivers but the open source ati or radeon or radeonhd driver is fully functional for that card. There are a zillion threads around here about that.

To get your sound working go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

You can look in the Multimedia and Video forum for more help with sound and video.

So basically I have no control over my video card settings? how do even know if it is active? ill be looking for a new video card soon anyways. I guess Ill have to consider if it will work well with ubuntu or not.

---

### Post by markbuntu on 2009-04-06
> **portdizzal said:**
> So basically I have no control over my video card settings? how do even know if it is active? ill be looking for a new video card soon anyways. I guess Ill have to consider if it will work well with ubuntu or not.

No, that is not the case. What you need to do is search the multimedia and video forum and you will find directions for using the open source drivers which work better for that card than the old ones from ati that did support it.

---

