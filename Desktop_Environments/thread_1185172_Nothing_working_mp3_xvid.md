---
title: "Nothing working mp3 xvid"
date: 2009-06-12
forum: Desktop Environments
---

### Post by gauravwaghmare on 2009-06-12
[SIZE=4]Hello! 
 I   am  new  to  ubuntu and after iiinstallling it on my PC I found that mp3 and Xvid files are not working+ the file manager//browser  report a problem are not working. The 'Places' menu is completely not workin. Please help  so that I can wipe out xp from my computer. Thanking you.
[/SIZE]

---

### Post by andrea000 on 2009-06-12
first things first check to see that

gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly-multiverse
are installed in synaptic
systems->administration->synaptic package manager

---

### Post by gauravwaghmare on 2009-06-13
> **andrea000 said:**
> first things first check to see that

gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly-multiverse
are installed in synaptic
systems->administration->synaptic package manager

I checked it and they are not their what should I do next? Please Reply.  I am using Ubuntu 9.04 Jaunty Jackalope.

---

### Post by TrakerJon on 2009-06-14
Start by going to System > select Administration > select Software Sources > Check the first four boxes under the Ubuntu Software and Updates tabs > Close and Reload

I suggest getting all available Ubuntu updates at this point, look for the update notification icon on the task bar. Reboot after updating your system and then install as many of the following as you wish.

Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) or if you have Ubuntu 9.04 "Jaunty Jackalope" simply do the following from a terminal window:

**sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list**

**sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update**

Several codecs and plug-ins are needed for playing a variety multimedia formats correctly...
**sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-plugins-farsight gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools**

Install these as well (some may already be installed at this point, no worries)
**sudo apt-get install realplayer w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev jackd sidplay-base xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin**

Adobe Flash too…
**sudo apt-get install flashplugin-nonfree**

Install the latest Sun Java JRE
**sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts**

---

