---
title: "Ubuntu 8.10 on Dell Studio 15 (1555)"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Plasma_Snake on 2009-05-08
I recently purchased Dell Studio 15 installed Ubuntu 8.10 on it. Everything worked fine, right out of the box, LAN,WiFi,Bluetooth even. Audio is acceptable too BUT the problem now remains with Webcam and GPU where GPU is the priority. I got ATi HD4570 512MB GDDR3 one. The DVD I got with the laptop has got some Intel 4500MHD and some Nvidia drivers, no ATi drivers and drivers too are in 2 separate folders, one for RHEL and other some SLED. Since I'm a n00b in the Linux department, I don't know much. So please tell me from where and how to get my graphics card drivers working? 
As u can see from the screen shot, even the display is not being detected, please tell me how to get all of it working

---

### Post by superm1 on 2009-05-08
Just use the System->Administration->Hardware Drivers tool

---

### Post by Plasma_Snake on 2009-05-08
Bumping for response!

---

### Post by Plasma_Snake on 2009-05-09
I did what u said and this is what I got:

---

### Post by Plasma_Snake on 2009-05-09
Bumping for Response.

---

### Post by Plasma_Snake on 2009-05-10
Mayday Mayday, please someone respond!

---

### Post by Plasma_Snake on 2009-05-10
No response??? Somebody please reply! :(

---

### Post by coffeeaddict22 on 2009-05-11
Open up a terminal, type in ```
lshw -C display
``` and post the result back.  It'll give detailed info about what graphics card the kernel thinks you've got...

---

### Post by Plasma_Snake on 2009-05-11
OK, here's the screenshot. As I and u all can see, it is detecting the ATi card but something else is also missing here that's why no option or way mentioned to install CCC. Moreover the screen has not been detected. So now how to fix it?

---

### Post by coffeeaddict22 on 2009-05-11
Looking around, your graphics card only hit the market in Jan 09, so an OS that hit the market in Oct the year before is probably not the best choice... have you tried upgrading to 9.04?  You might also want to take a look at this article...[here]("http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html") which seems to have found a hot-off-the-press repository for video drivers.

---

### Post by Plasma_Snake on 2009-05-11
I got the Jaunty DVD in mail yesterday only but haven't upgraded yet for 2 reasons:

[LIST=1]
[*]Got my project in 8.10 so dunno if I can retain it after upgrade or would I have to make it again from scratch?
[*]Lot of folks are having issues getting their LAN and WiFi working on Jaunty so fearing that mine might also go kaput, haven't upgraded it as they say, If it ain't broke, don't fix it.
[/LIST]
Will let u know the results of the operations mentioned in that link, as soon as I get back from my college.

---

### Post by coffeeaddict22 on 2009-05-11
Most of the LAN/Wifi problems are due to either odd setups, or upgrades with ndiswrapper in the prev setup.  Run the live CD if you´re worried.  The Wifi drivers have improved out of sight in the last 12 months, so I´m fairly certain you won´t have problems on a new box.  Display is in a bit of a fizz at present; ATI and NVIDIA are both humming and ha-ing about their Linux drivers, so it´s a little more difficult; you shouldn´t have any problems with it running on the default drivers, but you may not get all the eye candy for a while.

---

