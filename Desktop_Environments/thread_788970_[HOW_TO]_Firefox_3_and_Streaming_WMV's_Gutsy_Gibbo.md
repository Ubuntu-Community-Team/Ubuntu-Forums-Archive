---
title: "[HOW TO] Firefox 3 and Streaming WMV's Gutsy Gibbon"
date: 2008-05-10
forum: Desktop Environments
---

### Post by XanTrax on 2008-05-10
Ok well I am going to write this small yet simple tutorial since I seemed to have to go around to 10 places to get the answer.  On top of that, I couldnt really find a fix for Firefox 3 and streaming wmv's/videos.

Here we go:

First, install firefox 3



Open Synaptic -> Click "Settings" -> Click "Repositories" -> Click "Updates" tab -> Enable "Pre-release updates" and "Unsupported Updates"

Search firefox-3 -> Mark for install -> Click Apply



Second, install w32codecs


```

# sudo echo "deb http://packages.medibuntu.org/ gutsy free non-free" >> /etc/apt/sources.list

# wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

# sudo apt-get update

# sudo apt-get install w32codecs

```

This will install the w32codecs (obviously).

Now, lets install mplayer-plugin for Firefox

```

# sudo apt-get install mozilla-mplayer

```

This will install the MPlayer Firefox (2) plugin

Now we need to copy the plugin over

```

# cd /usr/lib/firefox/plugins

# sudo cp -r mplayerplug-in-dvx.so /usr/lib/firefox-3.0-3.0b4/plugins/
# sudo cp -r mplayerplug-in-dvx.xpt /usr/lib/firefox-3.0-3.0b4/plugins/
# sudo cp -r mplayerplug-in-qt.so /usr/lib/firefox-3.0-3.0b4/plugins/
# sudo cp -r mplayerplug-in-qt.xpt /usr/lib/firefox-3.0-3.0b4/plugins/
# sudo cp -r mplayerplug-in-rm.so /usr/lib/firefox-3.0-3.0b4/plugins/
# sudo cp -r mplayerplug-in-rm.xpt /usr/lib/firefox-3.0-3.0b4/plugins/
# sudo cp -r mplayerplug-in.so /usr/lib/firefox-3.0-3.0b4/plugins/
# sudo cp -r mplayerplug-in-wmp.so /usr/lib/firefox-3.0-3.0b4/plugins/
# sudo cp -r mplayerplug-in-wmp.xpt /usr/lib/firefox-3.0-3.0b4/plugins/
# sudo cp -r mplayerplug-in.xpt /usr/lib/firefox-3.0-3.0b4/plugins/

```

Those are all the necessary files for the MPlayer plugin

This part may not be needed but you can do it if you like.

```

# wget http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2

# tar -xvjf essential-20071007.tar.bz2

# sudo mkdir /usr/lib/win32

# sudo cp -r essential-20071007 /usr/lib/win32

```

Restart Firefox 3 and it should be working.

(P.S. I did this really early in the morning so I duno if thats right...but, it should be)


Like I said, there may be an easier way of some sort but I couldn't find one.  I tried installing VLC Plugin for Firefox and copying that over and it didnt work, same with Totem.  After I installed the w32codecs from the repo's, Firefox stopped crashing.

---

### Post by XanTrax on 2008-05-10
Huh, I thought more people woulda needed this.  Sorry for the bump too, I guess.

---

### Post by Ferux on 2008-06-19
Sorry, it didn't work for me.

---

### Post by XanTrax on 2008-06-19
Well, with Hardy Heron 8.04 this seems pre-resolved.  This was done when I was on 7.10 and upgrading to the Firefox 3 beta (whichever was the latest).  What happened for you?

---

