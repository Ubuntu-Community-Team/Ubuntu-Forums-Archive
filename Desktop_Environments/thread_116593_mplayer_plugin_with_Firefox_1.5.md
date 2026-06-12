---
title: "mplayer plugin with Firefox 1.5"
date: 2006-01-13
forum: Desktop Environments
---

### Post by gary_emms on 2006-01-13
I've just installed Mplayer usinf Automatix and it works fine except for the Firefox plugin (the video is choppy and the sound seems to come from an echo chamber). I've added srate=48000 to the config file with no success. I would like to remove the plugin and use Realplay (as this works fine) but I can't see how to do this inFF1.5.
Can any one help please?

---

### Post by art on 2006-01-13
I did enable RealPlayer to play the files it's associated with. You need to do 

sudo gedit  /etc/mplayerplug-in.conf

and look for line saying **#enable-rm=0(maybe 1)**, and change it to 

enable-rm=0

Now RealPlayer will do it's job. I hope you have also linked all the plugins from RealPlayer directory to /opt/firefox/plugins. Should work!

---

