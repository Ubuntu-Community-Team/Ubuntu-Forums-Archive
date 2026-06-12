---
title: "[SOLVED] Don't know how to set up wireless when installing Debian"
date: 2007-11-20
forum: Debian
---

### Post by doowgof on 2007-11-20
Hi all, I'm a newcomer of Linux. I've only used Ubuntu for about a week. I heard Debian is very stable therefore I'd like to switch to it now. However when I was installing Debian from a CD the system could not set up my wireless internet itself, and then I had to configure it. But then a problem came up, the system did not ask for my wireless SSID at all! How can I configure my internet then?

---

### Post by Majorix on 2007-11-21
Debian doesn't support wireless very well. I don't have a Debian installed anywhere nearby, so I can't help you with it right now, but take my word for it that Ubuntu is still one of the best when it comes to laptop support, but even Ubuntu has its flaws. So as a new-comer, I wouldn't start out with Debian. Ubuntu is pretty much like Debian, but more newbie-friendly.

---

### Post by b9anders on 2007-11-21
what hardware do you use? you might need to download some firmware in order to activate it.

You can use debian as a beginner, but there might be a slightly steeper learning curve as some things aren't preloaded like they are in ubuntu for philosophical reasons and the setup is more vanilla. If you're prepared to do a bit more legwork and asking for help in setting things up initially,you will however find yourself with a distro that is indeed as stable as any OS you can get, if that is what you want and an absolute breeze to maintain from thereon.

---

### Post by doowgof on 2007-11-21
Thank you guys! I guess I will use Ubuntu for some time, and then when I'm ready to learn more things I will then try Debian.
BTW: I'm using toshiba M30 laptop and I'm not quite sure what wireless device I'm using..

---

### Post by Antman on 2007-11-21
> **doowgof said:**
> Thank you guys! I guess I will use Ubuntu for some time, and then when I'm ready to learn more things I will then try Debian.
BTW: I'm using toshiba M30 laptop and I'm not quite sure what wireless device I'm using..

# 15.4¨ WXGA screen (1280 x 800), with TruBrite
# 1.6 GHz Pentium M 715 CPU (1Mb L2 cache)
# 512Mb DDR PC2700 ram (1x512Mb), expandable to 2048Mb.
# 80 GB 4200 rpm HDD (Toshiba MK8025GAS)
# 64Mb DDR NVIDIA GeForce FX GO 5200
# Intel 2200bg wireless, 100/10 built-in wireless and internal V.92 data/fax modem

---

### Post by doowgof on 2007-11-21
> **Antman said:**
> # 15.4¨ WXGA screen (1280 x 800), with TruBrite
# 1.6 GHz Pentium M 715 CPU (1Mb L2 cache)
# 512Mb DDR PC2700 ram (1x512Mb), expandable to 2048Mb.
# 80 GB 4200 rpm HDD (Toshiba MK8025GAS)
# 64Mb DDR NVIDIA GeForce FX GO 5200
# Intel 2200bg wireless, 100/10 built-in wireless and internal V.92 data/fax modem

WOW! Thank you mate! 
I guess there is a small difference cos I upgraded my momory to 1Gb

---

### Post by stunner on 2007-11-21
I started out on debian myself (still run it as well), but thankfully I didn't need wireless in those days.  You could start [here]("http://ipw2200.sourceforge.net/") for the drivers; debian also has a page [here]("http://packages.debian.org/ipw2200").

Also, what version of debian are you planning running?  Here's a link that may help for etch: [http://forums.debian.net/viewtopic.php?p=108833&sid=c7262df5dd267ffb7d8791648fb0af36]("http://forums.debian.net/viewtopic.php?p=108833&sid=c7262df5dd267ffb7d8791648fb0af36")

In any case - debian is fantastic, but if you're expecting a gui to ask you for ssid and other info, you're likely better off with ubuntu.

---

### Post by doowgof on 2007-11-21
> **stunner said:**
> I started out on debian myself (still run it as well), but thankfully I didn't need wireless in those days.  You could start [here]("http://ipw2200.sourceforge.net/") for the drivers; debian also has a page [here]("http://packages.debian.org/ipw2200").

Also, what version of debian are you planning running?  Here's a link that may help for etch: [http://forums.debian.net/viewtopic.php?p=108833&sid=c7262df5dd267ffb7d8791648fb0af36]("http://forums.debian.net/viewtopic.php?p=108833&sid=c7262df5dd267ffb7d8791648fb0af36")

In any case - debian is fantastic, but if you're expecting a gui to ask you for ssid and other info, you're likely better off with ubuntu.

Thank you!

---

### Post by b9anders on 2007-11-22
getting your wireless to work then is fairly simple. Simply install the ipw2200 firmware in /lib/firmware then run as root:

modprobe -r ipw2200
modprobe ipw2200

e voila. it is up and running.

---

### Post by doowgof on 2007-11-22
> **b9anders said:**
> getting your wireless to work then is fairly simple. Simply install the ipw2200 firmware in /lib/firmware then run as root:

modprobe -r ipw2200
modprobe ipw2200

e voila. it is up and running.

OMG! This is great! Thank you!

---

### Post by b9anders on 2007-11-23
you're welcome. :)

---

