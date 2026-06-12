---
title: "how to insatll windows media player?"
date: 2009-05-28
forum: General Help
---

### Post by tony12 on 2009-05-28
Hi Everyone!

I would like to install windows media player on ubuntu 9.04. would you please let me know how?  I know I need wine to do so and I have installed that. But how to validate windows media player? I like wmp and just want it.


Thank you

---

### Post by x33a on 2009-05-28
take a look here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8150](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8150)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3212](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3212)

i don't think it is stable even with wine though. if you want a nice multimedia experience, you'll have to use a linux alternative.

---

### Post by kulturloseramerikaner on 2009-05-28
> **x33a said:**
> 
i don't think it is stable even with wine though. if you want a nice multimedia experience, you'll have to use a linux alternative.
Agreed!  Once you see some of the alternatives, you won't even miss it.  For a full-featured media center try XBMC.  If you just want something quick and dirty to play songs, try Audacious or if you need to sync with an iPod go for Amarok.  And of course, the granddaddy that can play just about everything, VLC.

---

### Post by joe26 on 2009-06-18
another one is vlc media player

---

### Post by MyR on 2009-06-18
Amarok it the best media player I've ever used.  But if you really "like wmp and just want it" then you'll just have to stick with using windows.

peace

---

### Post by t4thfavor on 2009-06-18
I know its not the most popular, but I have been using Rhythmbox for a while, and it works pretty good. And its already pre-installed if you have regular Ubuntu.

---

### Post by synapsys on 2009-06-18
Windows media player is the devil! :evil:

---

### Post by TrakerJon on 2009-06-18
If your issue is that you want to play Windows media this should help otherwise you'll probably be stuck with Windows media player 6.4 and wine.

Start by going to System > select Administration > select Software Sources > Check the first four boxes under the Ubuntu Software and Updates tabs > Close and Reload

I suggest getting all available Ubuntu updates at this point, look for the update notification icon on the task bar. Reboot after updating your system and then install as many of the following as you wish.

Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) or if you have Ubuntu 9.04 "Jaunty Jackalope" simply do the following from a terminal window:

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Mplayer, several codecs and plug-ins are needed for playing a variety multimedia formats correctly...
**sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-plugins-farsight gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools sudo apt-get install w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev sidplay-base xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin**

---

### Post by MyR on 2009-06-18
> **synapsys said:**
> Windows media player is the devil! :evil:

Don't be jealous that WMP can play DRM-protected music and yours can't. :P

---

