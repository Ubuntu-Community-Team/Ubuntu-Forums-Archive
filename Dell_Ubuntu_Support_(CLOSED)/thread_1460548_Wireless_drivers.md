---
title: "Wireless drivers?"
date: 2010-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by neodudecurt on 2010-04-22
I have a Dell Studio 1535, and I recently installed 64-Bit Ubuntu 9.10 onto a partition to check out the difference between it and 9.04. For some reason, the wireless card appears not to be detected, or if it is, the driver isn't working properly. Does anybody know what I can do to get the wireless working on here?

Thanks a lot,
Curtis

---

### Post by Kai Summers on 2010-04-23
Have you checked the Hardware Drivers menu under System -> Administration, It may be using a proprietary driver - Check to see if it is and whether or not there are more than one to choose form, if there is try disabling the existing proprietary driver and selecting one of the other ones.

---

### Post by neodudecurt on 2010-04-23
I did check that out, and according to Ubuntu there are no proprietary drivers in use at all. Did you guys manage to work out the kinks with ATI, because if not then I also am apparently lacking a video card driver (Well alright, only insofar as 3D accelerated graphics go, but hey, those are important). Thanks for the suggestion though, everything helps.

---

### Post by Megaptera on 2010-04-23
I know this link talks about Dell Mini but it works fine on my Dell Inspiron. Don't forget to re-boot as it says on completion:

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Works in 9.10 & 10.04 Beta

---

### Post by marco.cervantes on 2010-04-23
What is the wireless card you use? to find out do this:

open terminal and type

sudo lshw -html > hardwareprofile.html

then go to your Home folder and open the HTML file and look for your wireless card and post it here.

---

### Post by shaka_zulu on 2010-04-24
What wireless card you have? I have Dell XPS and intel wireless card and it worked out of the box. Anyways check for solution here

[http://www.ubuntu-how-to.com/2010/04/ubuntu-driver-ndiswrapper-wifi-card.html](http://www.ubuntu-how-to.com/2010/04/ubuntu-driver-ndiswrapper-wifi-card.html)

---

