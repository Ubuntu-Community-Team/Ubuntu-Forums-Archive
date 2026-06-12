---
title: "ubuntu 10.4 and latitude c400"
date: 2012-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zippytex on 2012-02-15
I finally got my little Dell Latitude c400 working with Ubuntu 10.4 and it is wonderful!  I looked all over the web and finally found a way to do it.

Boot the live Ubuntu 10.4 disk

Look down at the bottom of the screen in the middle
A little graphic will appear

hit the space bar (also it will ask you to choose your language, just hit enter.)

Also, you click on the live cd line, not the install line.  You have to wait to install it from the icon on the desktop.  It won't do it otherwise.  

Then click on F6 and a screen will pop up, ignore it.
Hit escape button once.

type the following   i915.modeset=0 (that is a zero)  don't type anything else, just hit the return key.  (don't enter xforcevesa)  Even if you don't see a place to type, by the time you enter i915...., you will see where it is.

This works on my Dell Latitude c400 with the intel 830 graphics card.
After I installed it and rebooted, I never had another problem with the display.

I only know enough to barely keep my head above water.  I am sure someone else could do a better job on these instructions.  Hope this helps.

The laptop will boot up and give you a good screen.  It will adjust on and off during the process.  Be patient and wait until the desktop appears.

---

