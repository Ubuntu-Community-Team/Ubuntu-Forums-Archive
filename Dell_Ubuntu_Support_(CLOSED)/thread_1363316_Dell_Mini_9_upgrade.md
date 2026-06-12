---
title: "Dell Mini 9 upgrade???"
date: 2009-12-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by GaryS1953 on 2009-12-24
I just got a Dell A90 and like Ubuntu 8.04 that it came with, but I have one problem. I don't understand what it takes to upgrade the Flash Player so that I can watch Hulu video. I'm brand new to Ubuntu, and confused about all the options. Should I try to sort out the Flash Player issue, or would it be better just to upgrade to a newer version of Ubuntu, such as 9.04 or 9.10, and if so, should I do Netbook remix or the the standard version? I've also thought about going the Hackintosh route, but I would like to stay with Ubuntu if I can solve the video problem. Thanks!

---

### Post by Cowchip7 on 2009-12-24
I have Dell's 8.04 and can play video's on Hulu. What exactly is the problem you're having?

---

### Post by Cowchip7 on 2009-12-24
I see that you are brand new to Ubuntu. As I stated above, I am using Dell's lpia version that came with the mini. I chose to keep this version because it runs without any hiccups. A lot of people will encourage you to install the regular version. There are pros and cons to each version.

Dell's lpia:
PROS- supposedly made to work well with the atom processor, giving you increased battery life; odds are you will not run into compatibility issues with updates; all codecs are pre-installed and ready to go.

CONS- The repository is run by Dell so updates are far and few between. If you want the latest updates, you need the regular version. I am still waiting for an updated Rhythmbox player!

If you want to install the regular version, ubuntumini.com is a great source of information.

Now for some tips. I don't like the netbook GUI that Dell uses. So I switched it by clicking on Applications and "Switch Desktop Mode."

Next, make sure your system is up to date by clicking System-Administration-"Update Manager."

Once you update, give Hulu a go.

---

### Post by GaryS1953 on 2009-12-24
Actually the site I'm having problems with is fancast.com whcih reports that I need Flash 10.0.22.  I've tried updating Flash but Fancast still will not play their videos.  In my research it seems a lot of people have had problems with Flash and Dell version of 8.04.

You are right about the Dell GUI.  I didn't care for it either and the first thing I did was look for and switch desktop mode.

I did update by going to the update manager, but that also didn't make a difference.

Thanks so much for your suggestons.

---

### Post by grandma_kat on 2009-12-25
I got a Mini 9 for my granddaughter for Christmas, and installed Ubuntu 9.10 in a partition, double-booting with the pre-installed Ubuntu 8.04.  As noted by previous writers, Dell's 8.04 is a little tacky, although it seems to function just fine. 9.10 is great, but when I fired it up, it didn't see the wireless card. So I'm really glad I left 8.04 on the machine. But now I'm wondering where to find the drivers or even the specs for the wireless card. Anyone have a hint for me? What else is likely to be broken? I assume most of the problems will be the result of missing drivers, right?

Edited to add this:
I have an Asus EeePC 900A with Ubuntu 9.10 installed. It also runs on an Atom processor, but it doesn't have any problems seeing its wireless card.

---

### Post by grandma_kat on 2009-12-25
I found an answer to my question about getting wireless to work under Ubuntu 9.10 on the Mini 9.  See [http://is.gd/5AQnO]("http://is.gd/5AQnO") for the instructions at ubuntumini.com.  I haven't tried this yet, but it looks promising. According to the post, 9.10 has a bug that makes it not see the wireless card, but the fix is supposed to be easy. Yay!

---

### Post by JC Cheloven on 2009-12-26
> **grandma_kat said:**
> I found an answer to my question about getting wireless to work under Ubuntu 9.10 on the Mini 9.  See [http://is.gd/5AQnO]("http://is.gd/5AQnO") for the instructions at ubuntumini.com.  I haven't tried this yet, but it looks promising. According to the post, 9.10 has a bug that makes it not see the wireless card, but the fix is supposed to be easy. Yay!

Right, as a previous poster said, the solution can be found at [ubuntumini]("http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html")

But the info there no longer applies actually (I've found it yesterday): A wired connection of the mini9 triggers the "hardware drivers needed" message, and all you have to do is click on it to install the missing one. 

Cheers

---

### Post by nanotube on 2010-02-02
i would actually heartily recommend ditching the "dellbuntu" 8.04 and going for a stock install of the latest ubuntu. 

did that on my a90, and am quite happy with it. just had to tweak the sound conf to work, and install the bcmwl-kernel-source package to get the wifi to work. 

my writeup of the whole deal is on this forum thread:
[http://ubuntuforums.org/showthread.php?t=1389877](http://ubuntuforums.org/showthread.php?t=1389877)

---

### Post by GaryS1953 on 2010-02-02
> **nanotube said:**
> i would actually heartily recommend ditching the "dellbuntu" 8.04 and going for a stock install of the latest ubuntu. 

did that on my a90, and am quite happy with it. just had to tweak the sound conf to work, and install the bcmwl-kernel-source package to get the wifi to work. 

my writeup of the whole deal is on this forum thread:
[http://ubuntuforums.org/showthread.php?t=1389877](http://ubuntuforums.org/showthread.php?t=1389877)
That's actually pretty much what I ended up doing, though I had tons of trouble 9.10 and ended up going to 9.04.  Now everything is working great.  My only concern is upgrading when the time comes to the next LTS, I won't have the current install in place and that may make the upgrade more difficult.  

Great writeup by the way.  Thanks!

---

### Post by nanotube on 2010-02-02
> **GaryS1953 said:**
> That's actually pretty much what I ended up doing, though I had tons of trouble 9.10 and ended up going to 9.04.  Now everything is working great.  My only concern is upgrading when the time comes to the next LTS, I won't have the current install in place and that may make the upgrade more difficult.  


just try everything out using a livecd (or liveusb) before upgrading, to make sure stuff works (or that you can make it work). if it works on liveusb, it will work on an install.

and back up your data - that way you won't lose anything even if things go brown and stinky.

> 
Great writeup by the way.  Thanks!

glad you like :)

---

