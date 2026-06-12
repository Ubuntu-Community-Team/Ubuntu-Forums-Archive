---
title: "Esperanto Keyboard on Dell Mini 9"
date: 2009-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by inac on 2009-06-24
I'm remapping my Dell Mini 9 Laptop, so that the vestigial Windows key does something. In this process, I'm delighted to find that on top of the screen are options for Esperanto circumflexes! 

I can't figure out how to activate the circumflexes though... Could someone tell me how to type the cx's with the hat on it (etc)? Thanks!

---

### Post by coffeeaddict22 on 2009-06-25
Hi,
First of all, if you're googling around, be aware xorg.conf has been deprecated (read dropped) and HAL is the new standard when it comes to input devices, as of about 6-12 months ago.  A lot of the info out there is out of date.  If you're interested, a couple of references are [here on the Debian site]("http://wiki.debian.org/XStrikeForce/InputHotplugGuide") and [on the Ubuntu wiki site here]("https://wiki.ubuntu.com/X/Config/Input")
Before you go messing around in the bowels of HAL, however, most of the Keyboard settings are in System/Preferences/Keyboard, and by choosing a suitable international keyboard you should get the options you want.  You may need to go into languages and choose an appropriate one as well.
For the international keyboards, there are up to 5 options for every key; usually they're accessed by pushing the key a second/third/fourth/fifth time.
Post back if you need more help.

---

