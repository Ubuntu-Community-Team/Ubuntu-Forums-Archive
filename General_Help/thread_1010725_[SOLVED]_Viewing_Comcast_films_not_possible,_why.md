---
title: "[SOLVED] Viewing Comcast films not possible, why?"
date: 2008-12-14
forum: General Help
---

### Post by Camilia on 2008-12-14
I am unable to view films at comcast.net  When I click on film at comcast I get a black page. No prompts.

I have downloaded Java-gcj-compact-plugin, Free-java-sdk, and free flash plug. Went to adobe and downloade flash player and got message the adobe flash player 10 was already downloaded. Also went to youtube and downloaded the programs to view the films. I can view films at you tube. 

What else is there to download to view films at comcast.net?

---

### Post by hikaricore on 2008-12-14
Assuming you're using firefox, does this work in firefox on a Windows system?

I'm thinking perhaps they have agent checks on their site looking for the browser name or the OS.
If for example the site only work in IE on Windows you may have to install the firefox user agent addon to fake IE.

Just a thought.

---

### Post by Camilia on 2008-12-14
I only have ubuntu on my computer. I have just rebooted it. Previously had no problems viewing films at comcast after downloading the flash player.

I notice another person having the same problem viewing youtube. 

He had tried the command:
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

Got message that I had that plugin already installed.

He was given instructions to paste this:
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

I tried this and got info that I didn't have the programs. So I check the programs and downloaded  icedtea-gcjwebplugin
Now I can view films at comcast

---

