---
title: "New Dell XPS 15z with Ubuntu"
date: 2011-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tsega on 2011-07-20
Has anyone here tried the new Dell XPS 15z with Ubuntu. I am looking for a new laptop and I was wondering if the Dell XPS 15z works perfectly with Ubuntu. I just can't image going back to Windows, not for any machine.

---

### Post by Tsega on 2011-07-20
Is it just me or Ubuntu Forums no longer the place find answers regarding Ubuntu?

---

### Post by ferrangil on 2011-07-22
I managed to install it, using half of the space, but then when I restart and ubuntu should launch, I just get a black screen and nothing happens. You should install it with one specific option as stated here [https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z) but anyway, still not able to pass that black screen...
Recovery mode shows a few lines but finally gets stuck the same way.
Any ideas?

---

### Post by Tsega on 2011-07-26
> Any ideas? 

Sorry but I have none. On top of your question, here is what I want to ask the community at large, why does the lack of proper support from hardware manufacturers hinder us (Ubuntu users) from having a stylish, top quality product that we can use with pleasure just like we do our operating system?

There was an initiative started by Mark Shuttlesworth a while back, addressing this same issue but I see that it hasn't been resolved. What's the update on that? I feel my love of Ubuntu is making me lose on a great number of hardware selections. 

Please feel free to share your thoughts on the perfect laptop, mine is close to the Dell XPS 15z, thin, light, high performance, stylish and solid aluminum body and of course fully compatible with Ubuntu.

---

### Post by melcior on 2011-09-26
My Dell xps 15z only runs partially with ubuntu 11.10 beta2:
1.-only a single core recognized despite last SMP kernel
2.- after Beta2 upgrade network fails
3.- heating problems CPU 73 celsius
4.- battery less than 2 hours autonomy
5.- lot of crashes when the system starts.
6.- skype dosn't runs
7.- one of the mandatory things each day is to look for new failures and googling to try if someone has solutions.
8.- I tried 11.04 installation but is not operational on this machine.
9.- printing is in bad quality if you compare the same document printed from windows.

At least till now for me is a lucky solution to have enough room in this "fancy machine" for windows 7 when I need to work.
The comparison in performances and hardware performances are clearly better in windows.
There is no support from Dell to put the machine at the same level in Ubuntu

In my opinion Ubuntu runs well in older machines, but newest are out of performance, this is one of the major drawbacks. I have and older Dell XPS M1530 runnig 11.04 and no problems. May be my fault is to upgrade my machine earlier than ubuntu has enough kernel support.
My recomendation : be patient and use other hardware.

---

### Post by christianhland on 2012-01-21
I just got a Dell XPS 15z as well. Reading some threads on here helped me installing Ubuntu, but it has several problems, the touchpad being the most crucial one at the moment. 

I got the touchpad working, but it is only recognized as an external mouse instead of as a touchpad, meaning I can not use features such "disabling touch to click" and "disable while typing". These are crucial features when the touchpad is so large and it's hard to work efficiently without them because the cursor flies everywhere.

But at least it was usable. Yesterday there where a new kernel update and some other updates, these may have screwed something up because today the touchpad is not working as it should.

Whenever I move the cursor using the touchpad and remove my finger, the cursor jumps back to its previous position. This is terribly annoying and renders the touchpad unusable..

Does anybody have a solution to this problem? And can it be expected that there will be drivers written that support this piece of hardware? 

Any help would be appreciated, 

Chris

---

### Post by AnthonyAlmighty on 2012-01-25
> **Tsega said:**
> On top of your question, here is what I want to ask the community at large, why does the lack of proper support from hardware manufacturers hinder us (Ubuntu users) from having a stylish, top quality product that we can use with pleasure just like we do our operating system?

There was an initiative started by Mark Shuttlesworth a while back, addressing this same issue but I see that it hasn't been resolved. What's the update on that? I feel my love of Ubuntu is making me lose on a great number of hardware selections.

I feel you on this one. I just picked up an XPS 15z because of the specs, and I was really looking forward to loading up ubuntu; however, I ran into the same installation and boot problems that are listed here. 

I'm a software guy, and I know how important it is for my software products to work for our customers. I don't really fully fathom why we can't bring this level of "it just works" to linux. Especially Ubuntu. 

I have an Asus G74 that is my development rig, and it runs Ubuntu like a dream.  The installation and configuration is still light-years away from making the transition to linux as easy as going to Windows 7 or OSX Lion, and in my opinion, it should be. 

Windows is great for running the latest and greatest hardware on an inexpensive setup. You get hardware choice with Windows. 

OSX is great for running the latest and greatest hardware on a device with incredible polish. Macs are stylish, stable, but expensive machines. 

Linux, Ubuntu, realistically should exist in the middle. I want a "stylish" user experience and hardware, but at the price points of the PC--not the Mac.

---

### Post by luchobarrios on 2012-05-02
I have installed (k)ubuntu 12.04 LTS (I hate unity) and I did not have any problema. I installed bumblebee and I got high battery life. +4-5 hours. Actually hdmi, display port, and 9-1-cardReader don't work, and the trackpad works without multitouch.
I really recommend the last version of ubuntu =D

---

### Post by MikeM6244 on 2012-05-23
Hey guys...

I got Ubuntu 12.04 today on my XPS 15z. I read a few things (wikis and such) that said this version of Ubuntu didn't have many problems after installing. I chose the Windows installer option (I dual boot; I don't use any type of emulator).

Unfortunately, neither my touchpad nor my keyboard work. I've tried to find solutions to both of these, but haven't been successful.

This is what my terminal reads when I tried to fix the touchpad:

mike@ubuntu:~$ # sudo rmmod psmouse; sudo modprobe psmouse proto=imps
mike@ubuntu:~$ # sudo rmmod psmouse; sudo modprobe psmouse proto=imps/etc/modprobe.d/
mike@ubuntu:~$ sudo apt-get install telepathy-sofiasip telepathy-butterfly telepathy-idle libtelepathy-farsight0 python-tpfarsight
[sudo] password for mike: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mike@ubuntu:~$ sudo rmmod psmouse; sudo modprobe psmouse proto=imps


Hopefully you guys can help me out here! Thanks!

---

### Post by Tarangor on 2012-11-12
> **MikeM6244 said:**
> Hey guys...

I got Ubuntu 12.04 today on my XPS 15z. I read a few things (wikis and such) that said this version of Ubuntu didn't have many problems after installing. I chose the Windows installer option (I dual boot; I don't use any type of emulator).

Unfortunately, neither my touchpad nor my keyboard work. I've tried to find solutions to both of these, but haven't been successful.

This is what my terminal reads when I tried to fix the touchpad:

mike@ubuntu:~$ # sudo rmmod psmouse; sudo modprobe psmouse proto=imps
mike@ubuntu:~$ # sudo rmmod psmouse; sudo modprobe psmouse proto=imps/etc/modprobe.d/
mike@ubuntu:~$ sudo apt-get install telepathy-sofiasip telepathy-butterfly telepathy-idle libtelepathy-farsight0 python-tpfarsight
[sudo] password for mike: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mike@ubuntu:~$ sudo rmmod psmouse; sudo modprobe psmouse proto=imps


Hopefully you guys can help me out here! Thanks!

Hello, i just registered because i have the same problem you described, i know you posted that a long time ago, but if you could tell me how you solved that issue i'd be very gratefull. 
Thank you, i apologize if i have a bad english.

---

