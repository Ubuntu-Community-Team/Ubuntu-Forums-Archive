---
title: "Latitude e6510 latest Ubuntu 10.10 Installation problems"
date: 2010-10-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ramsrambo on 2010-10-11
Hi,

I saw that 10.10 was released and I decided to install on my Dell Latitude e6510.
So I downloaded the 64bit ISO image from ubuntu.com and I have installed on a USB stick.
While booting the machine I pressed F12 and selected to boot from the USB drive. I selected "Try ubuntu without installation" 

Initially I got the purple splash screen and there after it was blank screen. Then I finally heard from the speakers music we get when we boot Ubuntu machines.
After this I could not see anything at all. I was staring at a blank screen.

regarding my HW - Core i7 720QM, intel 57 chipset motherboard, 4gb RAM, track touchpad, bluetooth, intel wifi, Nvidia NVS 3100 M grpx card, 500gb hard drive, smart card slots, SD card slots, 

What exactly is missing here for this machine to boot ? Please suggest something

---

### Post by mörgæs on 2010-10-12
There are many reports indicating that the USB based boot does not work, but the CD based boot does. Have you tried this?

---

### Post by ramsrambo on 2010-10-12
Morgaes,

It worked on USB I just changed few parameters before it went to boot thats all.

Thanks for all the help.

Problem Solved 
Ram

---

### Post by mörgæs on 2010-10-13
Good, please mark the thread 'solved'.

---

### Post by luopio on 2010-10-16
would also be nice if you shared those "few parameters" so we others could make it work too :)


[EDIT] perhaps related to this [http://ubuntuforums.org/showthread.php?t=1369420](http://ubuntuforums.org/showthread.php?t=1369420). Remember this fixing my issues w/ 10.04 [/EDIT]

---

### Post by ramsrambo on 2010-10-18
Lupoio,

It is the nomodeset boot param that you need to change.

When you get the first purple screen hit F6 and you get this list of boot parameters. Just change this nomodeset param and then press ESC. After that boot the machine and it should work.

Thanks,
Ram

---

