---
title: "mplayer plug-in stuck at buffering 99%"
date: 2006-05-09
forum: Desktop Environments
---

### Post by dtux on 2006-05-09
Hi,

I'm new to ubuntu having mainly used red hat and suse. I find ubuntu really straight forward to use and I'm kinda getting used to apt-get. The ubuntu community seems really active and i've found help documentation easy to come accross.

However, I'm really stuck with trying to play mp3 files that are embedded on web pages with the mplayer plugin on firefox 1.0.8. I followed much of this how-to [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu) and got mplayer-386, mozilla-mplayer and mplayer-fonts installed along with the necessary mmedia codecs and lame etc. I can play mp3 files with mplayer and if I click on an mp3 link mplayer-plugin will play the mp3 file in a firefox window.

It just seems to be embeded mp3s that are a problem. Although, I can sometimes get the file to play if I right click on the mplayer plugin and select play before the buffering message gets to 99%. Also embed tags that don't have autostart=false seem to play ok.

I have tried installing mplayer-586 and tried different options in /etc/mplayerplug-in.conf but still no luck ](*,) 

Anyone got any ideas?

Thanks in advance

---

### Post by SmokinJuan on 2006-05-14
Just keep refreshing the page... sooner or later one of your refreshes will "catch" and your media will play.  Apparently, that's how the mplayer-plugin is supposed to work as I've not seen any other remedies in the other 10,000 pages I've seen on the topic. Good luck.

---

### Post by fubarbundy on 2008-01-29
See also [http://ubuntuforums.org/showthread.php?t=374925](http://ubuntuforums.org/showthread.php?t=374925)

---

### Post by gfahey on 2008-03-06
Right click directly in the screen and select "configure".

Then, under "video output" (from drop down menu) select "x11".

I've run into this issue a few times and this is a big part of the solution. I also only have the mplayer plugin for Firefox. Delete/remove any other Mozilla plugins for streaming video as these conflict with one another.

---

