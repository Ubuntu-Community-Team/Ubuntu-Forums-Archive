---
title: "Dell Latitude D610 New to Linux/Ubuntu"
date: 2011-10-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by djl236 on 2011-10-27
Hello all,
 
First time posting here. I'm a long time Windows user and a Windows System Admin by trade that wants to dive into Ubuntu in my free time. I have an old Dell Latitude D610 laptop with 2 GB of RAM and an Intel Centrino processor in it (I forget the speed I think it may be 2.0 or 2.26 GHz. I believe the graphics chipset is Intel as well.
 
Can anyone reccomend a good place to start diving in? What version of Ubuntu to use? I've heard from a few to stay away from 11.04 and 11.10 but I figured I'd ask here for advice.
 
Any help/advice apprieciated. If I posted this in the wrong forum, I apologize.
 
 
Thanks.

---

### Post by collisionystm on 2011-10-27
> **djl236 said:**
> Hello all,
 
First time posting here. I'm a long time Windows user and a Windows System Admin by trade that wants to dive into Ubuntu in my free time. I have an old Dell Latitude D610 laptop with 2 GB of RAM and an Intel Centrino processor in it (I forget the speed I think it may be 2.0 or 2.26 GHz. I believe the graphics chipset is Intel as well.
 
Can anyone reccomend a good place to start diving in? What version of Ubuntu to use? I've heard from a few to stay away from 11.04 and 11.10 but I figured I'd ask here for advice.
 
Any help/advice apprieciated. If I posted this in the wrong forum, I apologize.
 
 
Thanks.


use 10.04 LTS on that laptop.

I have a D531 ( similar model ) and it was slow with 11.10.

10.04 is reliable and a good starter.

---

### Post by djl236 on 2011-10-27
> **collisionystm said:**
> use 10.04 LTS on that laptop.
 
I have a D531 ( similar model ) and it was slow with 11.10.
 
10.04 is reliable and a good starter.
 
 
Thank you for the quick reply. I'm downloading an iso of 10.04 as I type this.

---

### Post by cespinal on 2011-10-27
use the live usb's with various flavours for you to try.... 

Im using the latest kubuntu in a very old laptop with 512 Mb RAM and slow centrino processor... works perfectly.

---

### Post by mörgæs on 2011-10-27
I have one of these. Recommending Xubuntu 11.04 (have not tried 11.10 yet).

---

### Post by collisionystm on 2011-10-27
> **djl236 said:**
> Thank you for the quick reply. I'm downloading an iso of 10.04 as I type this.

Excellent! I am sure you will enjoy.

Make sure to burn it to a CD... 10.04.3 is unfriendly with USB drive boots. 

The software repo in 10.04 is older than the latest versions, but you can easily install up to date versions with PPA's. 

For example, if you want the latest FIrefox browser, you would google for FireFox stable PPA.

The listing will lead you to this

> ppa:mozillateam/firefox-stable
[B]
You add it by opening a terminal and typing

[/B]```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```
Then do 

```
sudo apt-get update 
```

that will refresh your packages

```
sudo apt-get upgrade
```

^ will install latest packages
[B]

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[/B]

---

### Post by djl236 on 2011-10-27
Everyone thank you for all the quick replies. I can't wait to dive in.
 
I think I'll go with 10.04 for now, before trying out some of the alternative desktops like kubuntu, etc.

---

### Post by dFlyer on 2011-10-27
You might want to reconsider and try using 11.10 if your system can handle it. If not than try 11.04 as they contain the new interface that Ubuntu has switched to. Unity the new desktop environment does take a little getting us to, but once you do, it's very easy to navigate.

---

### Post by djl236 on 2011-10-27
> **collisionystm said:**
> Excellent! I am sure you will enjoy.
 
Make sure to burn it to a CD... 10.04.3 is unfriendly with USB drive boots. 
 
The software repo in 10.04 is older than the latest versions, but you can easily install up to date versions with PPA's. 
 
For example, if you want the latest FIrefox browser, you would google for FireFox stable PPA.
 
The listing will lead you to this
 
 
 
**You add it by opening a terminal and typing**
 
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```
Then do 
 
```
sudo apt-get update 
```
 
that will refresh your packages
 
```
sudo apt-get upgrade
```
 
^ will install latest packages
 
 
**[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)**

 
 
Excellent, thank you again. The terminal commands are something I need to get used to. So I can upgrade all the software without actually upgrading the OS itself to 11.04 or 11.10?

---

### Post by collisionystm on 2011-10-27
> **djl236 said:**
> Excellent, thank you again. The terminal commands are something I need to get used to. So I can upgrade all the software without actually upgrading the OS itself to 11.04 or 11.10?


You can install all of the software that comes with 11.04. But if you do that, you may as well use 11.04! lol.

11.10 ... no. It is based on a new version of gnome.

[http://Gnome.org](http://Gnome.org)

10.04.3, 11.04 and previous versions all used Gnome2. Gnome-3 is brand new and a completely different system.

---

### Post by djl236 on 2011-10-27
> **collisionystm said:**
> You can install all of the software that comes with 11.04. But if you do that, you may as well use 11.04! lol.
 
11.10 ... no. It is based on a new version of gnome.
 
[http://Gnome.org](http://Gnome.org)
 
10.04.3, 11.04 and previous versions all used Gnome2. Gnome-3 is brand new and a completely different system.
 
 
LOL gotcha. I'll just upgrade the essentials like FireFox

---

### Post by djl236 on 2011-10-28
I ended up upgrading 10.4.3. to 10.10 to get the Google Music integration app in the sound area of the upper menu bar. So far I'm liking it a lot. System is running very smooth.

---

### Post by collisionystm on 2011-10-28
> **djl236 said:**
> I ended up upgrading 10.4.3. to 10.10 to get the Google Music integration app in the sound area of the upper menu bar. So far I'm liking it a lot. System is running very smooth.

Very cool!

If you decide to do an 11.10 on their, I would try Kubuntu. KDE is much faster than Unity on the 11.10 release.

---

### Post by mörgæs on 2011-10-28
Good. If the problem is solved, please mark the thread so.

---

### Post by djl236 on 2011-11-02
> **collisionystm said:**
> Very cool!
 
If you decide to do an 11.10 on their, I would try Kubuntu. KDE is much faster than Unity on the 11.10 release.
 
 
 
Awesome I'll keep that in mind. In the mean time, I'll very pleased with Ubuntu 10.10 running Docky for a unity-like dock and some other theme customizations such as transparent windows like Win7, etc. Its very smooth on this older laptop. Thanks for all the help and advice!

---

### Post by alreadytaken4536 on 2011-12-25
I have this laptop and I too am trying to install Xubuntu 11.04 on it. Unfortunately, it tells me that I do not have the proper firmware to enable an internet connection. What can be done about this?

---

### Post by mörgæs on 2011-12-25
I would recommend Xubuntu 11.10. 

If you install this one using wired internet connection, do you get access?

---

