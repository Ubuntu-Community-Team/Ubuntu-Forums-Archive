---
title: "MP3 with Sound Juicer in Hardy..."
date: 2008-06-14
forum: Desktop Environments
---

### Post by neocortex on 2008-06-14
Hello!
Can anyone explain steps to make mp3 decoding/encoding possible in Sound Juicer. I saw HowTo-s for Gutsy and Dapper, but not for Hardy. I tried those older, but it is not working. I think key question is what gstreamer one should install and how to setup MP3 in Juicer's preferences.

Best,
PM

---

### Post by t0n1 on 2008-08-07
Good question, I was not able to get it working either.
Can anyone help?

---

### Post by Glw8z on 2008-08-08
Well, I hope you have medibuntu enabled in the third-party sources. 

This page will help you with that, if you haven't done it yet: [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu") 

Then to install the restricted packages, simple instructions are at: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats"). 

Find the right type of w32codecs and install them. As far as the gstreamer0.10-plugins, I have at least bad, base, good and ugly types. Perhaps you could try to play back some mp3 type file, and if you don't have the right codecs installed, your system will try to locate them (and install, if you instruct it to). I don't remember exactly which packages are essential for playing back and recording those mp3 files, but at least they're working with the above-mentioned packages/plugins. 

As far as selecting mp3 as the format of your choice in SoundJuicer, that's easy once the codecs are installed. You go to Settings and down to the format, where mp3 should be included in the possible formats along with Ogg and Flac (and perhaps Aac, if it's been installed as well). 

I don't know if this is the most elegant explanation for your procedure, but it should work.

---

### Post by NewDisciple on 2008-08-09
Make sure the Multiverse and Universe repositories are enabled.
Copy & paste the following in a terminal (for 32 bit):
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
> sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

If this doesn't work there is also a manual way of doing it.  These commands are for Ubuntu and will vary slightly for Kubuntu & Xubuntu.

---

### Post by svenskmand on 2008-08-13
Just wanted to say that if you haven't got the codecs from medibuntu installed then Sound Juicer will let you define a format present just fine, but even though it is activated it won't appear in the drop-down-list, and no warning is given that the codecs doesn't exists.

Just be aware of this, and that the solution is installing the missing codecs (it took me some time :S, maybe the Sound Juicer team should make this more clear in the menus (Is now reported in Launchpad [https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/257437]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/257437") )).

---

### Post by marshcast on 2009-01-19
> **svenskmand said:**
> Just wanted to say that if you haven't got the codecs from medibuntu installed then Sound Juicer will let you define a format present just fine, but even though it is activated it won't appear in the drop-down-list, and no warning is given that the codecs doesn't exists.

Just be aware of this, and that the solution is installing the missing codecs (it took me some time :S, maybe the Sound Juicer team should make this more clear in the menus (Is now reported in Launchpad [https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/257437]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/257437") )).

Not sure this is true (sorry), I have not medibuntu, but have installed the gstreamer...-bad-multiverse an the gstreamer...-ugly-multiverse packages and it works perfectly. 

The proper names of these packages can be looked up by 
1. enabling multiverse (in /etc/apt/sources.list OR system>admin>software sources) 
2, using the TAB key whilst entering the 'sudo aptitude install gstreamer0' bit of the install command (or Applications>ADmin>Software manager' (or similar) and looking for the packages.

sorry - bit long winded - wanted to get noobs thinking - let me know if it's a PITA :P

---

