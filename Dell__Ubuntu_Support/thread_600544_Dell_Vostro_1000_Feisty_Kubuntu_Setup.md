---
title: "Dell Vostro 1000 Feisty Kubuntu Setup"
date: 2007-11-02
forum: Dell  Ubuntu Support
---

### Post by whi+eNoi$e on 2007-11-02
Crash course in Dell Vostro 1000 Kubuntu 7.04 Feisty Fawn Setup

...more expensive Dell Vostro models supposedly come with Ubuntu as a choice for OS on purchase, and thus, probably have an easier time with a fresh installation of ubuntu and its ilk, but the low-cost/high-value Vostro 1000 (many nice gadgets for $550 new $450 refurbed laptop IMO) does not have that option so the setup seems to be more difficult due to "non-supported" ("cheaper") hardware.  I battled for two weeks to get kubuntu feisty running adequately, with only minor annoyances left to fix.

ndiswrapper will be used to load the windows driver for network card...for convenience here is link to Dell drivers

[http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=VOS_N_1000&os=WLH&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=VOS_N_1000&os=WLH&osl=en&catid=&impid=)

Also some ubuntu forums forget us KDE lovers and assume we were using the ubuntu GUI (gnome I believe?). at some point you may find that it is difficult to follow some guide simply because KDE is a little harder to administrate than gnome, i installed gnome just so i would have an easier route to administrate some system settings along the way. Maybe ignorance and overkill, but it was 3am and I was in my fourth hour on a particular problem and not being able to find a simple administration panel …overkill it would have to be...

--network--------++
Wired Ethernet worked out of the box…conveniently enough.
Wireless with the Dell-linux-unsupported 1390 broadcom driver did not work out of the box. 

excellent guide by peperdeisel for ndiswrapper for broadcom 1390 driver installation...
[http://ubuntuforums.org/showthread.php?t=297092&highlight=vostro+1000](http://ubuntuforums.org/showthread.php?t=297092&highlight=vostro+1000)

_wcid installation_
knetworkmanager was buggy and would not let me connect to encrypted networks at the time of writing (connection would freeze at assigning IP address then give fail message) so I used wcid to manage my wifi connections.
**NOTE using wcid will uninstall knetworkmanager and vice-versa

first install automatix to easily grab wcid and many other righteous system and software dev tools.

Automatix install guide written by arnieboy here
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

using automatix you should then be able to choose wcid from the network tools area. once installed wcid is easier to use than windows XP wireless configuration GUI!

--sound----------++
I was able to get mine to work out of the box (and after installing updates) but it required root privelages...no sound under normal circumstances, but when i attempted with root (and subsequently escalated my user to root privelages) --Voila!-- music to my ears. To test this, simply go to command prompt and type: 

sudo amorok

...don't need to load any music, there is a test audio file already loaded in the player. That was the end of sound troubleshooting for my part. Hopefully the same can be said for you. There are some other things that could be hindering your audio and many guides are available in ubuntu forums. I didn't ecounter them so I don't have specific guides to give you here. 
>sorry!<

--graphics-------++
Your ATI IGP Xpress 1150 needs to utilize a different driver if you need 3D graphics performance. If you are a light user, looking to simply browse the internet, check mail and word process, you don’t need to do anything here honestly. You will note that graphics work fine under the GUIs for low performance out of the box, but 3D rendering is slow and painful. this requires the restricted drivers suppositories to be enabled.

To enable restricted drivers This is where the gnome desktop came in handy for me. I could not find a ‘restricted drivers manager’ as being noted here:

[http://www.michaellarabel.com/?k=blog&i=114](http://www.michaellarabel.com/?k=blog&i=114)

so I installed gnome so that these instructions would apply to me. I am sure there is a file somewhere that allows you to quickly edit this in a command prompt, but ubuntu is supposed to be the Linux answer to the average Windows-what-the-hell-is-a-command-prompt user mentality. So if you don’t like it, go to Russia! –Homer J. Simpson

--Shutdown issue---++
One other major bother—perhaps you have already encountered this, was that at some point in these instructions my main user lost the ability to fully power off the laptop by using the KDE shutdown/hibernate/switch-user/etc panel. Not cool. You could unsuspectingly leave your hardware powered up with a black screen thinking you had shut it down. Why would you assume that Shut Down would mean shutdown? Many users report a black screen, but I simply get a repeating 10-20 second cycle of black screen, kde splash, black screen, kde splash…and so on.

I am still trying to get a solid fix on this but somewhere in the forums as I desperately tried to find a way other than manually powering off at the power button—I found the simple answer to hold me –and maybe you- over until the greater fix is found. Be prepared to shutdown, and then type:

Sudo shutdown –h now

This command tells the OS to stop AND the hardware to either HALT or POWER OFF according to the helpfile on shutdown, but the end effect is your machine rapidly will power off, still giving KDE a chance to detach.

Hope this newbie’s manual helped. It is the only reason I joined the forums. I figured that It would have been nice if I had found all these in one place. Many thanks to the authors of the individual guides. This post is nothing without their guidance.

Peace out,
jason++

---

