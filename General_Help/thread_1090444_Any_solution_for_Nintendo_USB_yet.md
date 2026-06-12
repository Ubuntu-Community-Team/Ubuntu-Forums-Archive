---
title: "Any solution for Nintendo USB yet?"
date: 2009-03-08
forum: General Help
---

### Post by Zieb on 2009-03-08
For a couple years now this has been my biggest problem with Linux, and in every thread I've found on this no solution is offered, and it seems most people don't understand the problem.  I guess most Linux people aren't videogame people, or at least aren't Wii people.  So here is the problem as clear as I can state it:

There is a Wi-Fi adaptor that plugs into your wired computer (through USB) to allow it to connect to your Wii, which has Wi-Fi.  This allows your Wii to go online and download great games like Megaman 9 and Star Soldier R.  Not to be able to connect the Wii to the internet is, thus, a problem.  

Here is some information on the adaptor:
[http://en.wikipedia.org/wiki/Nintendo_Wi-Fi_USB_Connector]("http://en.wikipedia.org/wiki/Nintendo_Wi-Fi_USB_Connector")

Here is the software that the Wi-Fi adaptor that plugs into your computer uses to talk to the Wii:
[http://www.nintendo.com/consumer/systems/wii/en_na/onlineUSBDownload.jsp](http://www.nintendo.com/consumer/systems/wii/en_na/onlineUSBDownload.jsp)

The software is Windows specific.  Thus, to have Ubuntu on your wired computer is to not be able to download the best games for the Wii.  

Thus, myself, and obviously other people on here, are wondering if there is a solution to this problem?  It is one of those things that keeps a solely Linux system off the table, even if we wanted it (or in my case, could convince the wife to go for it :)).

---

### Post by snkiz on 2009-03-08
First off I would suggest that you take the issue up with Nintendo.  having a windows only program for that is shortsighted on their part. secondly have you tried wine? This is just off the top of my head, your problem interests me so I'll have a look when I'm back on my desktop

Edit: OK so according to the info provided this thing is a piece of crap, and you don't even need it a wireless router will do. Nintendo has come out with a replacement router and the software hasn't been updated in over a year. If your bent on using it these links should help: [https://www.linuxquestions.org/questions/linux-hardware-18/nintendo-wi-fi-usb-connector-emulation-503394/]("https://www.linuxquestions.org/questions/linux-hardware-18/nintendo-wi-fi-usb-connector-emulation-503394/") and [http://ubuntuforums.org/showthread.php?t=418446]("http://ubuntuforums.org/showthread.php?t=418446")

---

### Post by miniyak on 2009-03-08
from citation 5 in your wikipedia link- [http://www.gamefaqs.com/portable/ds/file/925329/40161](http://www.gamefaqs.com/portable/ds/file/925329/40161)
By looking at the table of contents im going to say all the necessary info should be there. If you are hoping for a simple, install to gui solution it is probably not going to happen. Sometimes you get lucky though. These type of problems as a are defiantly learning experiences. If the guide is difficult please keep asking and keep posting

---

### Post by joey-elijah on 2009-03-08
I can see why this is annoying. 

i would certainly try it in WINE and e-mail Nintendo. Also, it might be worth posting in the gaming section of the forum as someone may know a workaround.

---

### Post by Paul S on 2009-03-17
No solution yet.  The problem is the wii will only connect to a wifi device in master mode, as explained in this link [http://www.gamefaqs.com/portable/ds/file/925329/40161](http://www.gamefaqs.com/portable/ds/file/925329/40161)   and master mode is not supported on all cards.  I checked my on board wifi  and get this error:

paul :~$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

which I guess means it can't work.

But then I see the hostapd program and this write up   [http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)    but I can't get hostapd to work either.

paul :~/Desktop/bld.hostapd/hostap/hostapd$ sudo ./hostapd ./hostapd-minimal.conf
Configuration file: ./hostapd-minimal.conf
ioctl[SIOCGIFFLAGS]: No such device
nl80211 driver initialization failed.

ideas?

---

### Post by RobOrr on 2009-03-17
I'm assuming of course that your problem is that you don't use a wireless network in your house? one of my friends was complaining that he had to buy (in his words) "some extra USB wifi connector" to connect his wii to his network (and thus to the internet). I quickly checked online and you can connect direct to any wireless network using the wii's internal card. Just thought I'd cover that base in case you have the same issue as my friend.

---

### Post by mb_webguy on 2009-03-17
My Wii connects automatically to my wireless router.  I don't see why it would be any different if I set my computer up as a WAP.  You should be able to bridge your wired and wireless interfaces, then use Network Manager to set up a new wireless network.  Personally, though, I'd just buy a cheap wireless router.

EDIT:  This [howto]("http://ubuntulinuxhelp.com/how-to-setup-a-wireless-ubuntu-router/") seems a bit overly complicated, but apparently does the job if you don't want to buy a router.

---

### Post by Paul S on 2009-03-18
Thanks for that link.

Yes, there are things I could buy to get it working, but, like many people, I'd prefer to use the equipment I already own.  The problem for me is my wifi card does not support "master" mode (at least out of the box).  But, there can often be ways to work around missing features to get things working.  That's where I'm searching now.

regards,

---

