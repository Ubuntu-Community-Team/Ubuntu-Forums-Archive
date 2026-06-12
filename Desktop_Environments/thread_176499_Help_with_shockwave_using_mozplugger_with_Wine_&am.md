---
title: "Help with shockwave using mozplugger with Wine &amp; Windoze Firefox"
date: 2006-05-14
forum: Desktop Environments
---

### Post by DarkStarDeity on 2006-05-14
I have followed the steps outlined [here]("https://wiki.ubuntu.com/RestrictedFormats#head-55dd46852b91060cde557660462b56e31cac305f") to try and get shockwave running in Firefox. I got the plugin installed for the Win version of Firefox and am up to the last step - configuring mozplugger to use it. I have edited the mozpluggerrc file as per the instructions, but it isn't working. I have taken a look at the pluginreg.dat and the new association is not appearing in it. What am I missing? How do I get the mozplugger plugin configured correctly to use this? 

I am running Breezy and using Firefox 1.5.03 updated from the Mozilla site as per [these instructions]("https://wiki.ubuntu.com/FirefoxNewVersion")

---

### Post by catlett on 2006-05-14
I don't know if it works when you already have 1.5 installed but Automatix installs firefox 1.5 and all it's plug-ins. [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by DarkStarDeity on 2006-05-14
Unfortunately, there is no native plugin for shockwave under linux (unlike shockwave flash, which does at least have an older plugin), which is why I'm going about this convoluted route to try and get it working. I already have the shockwave flash plugin working, it's shockwave itself I'm having trouble with. 

Just more info, I can use shockwave in the win version of firefox under wine, but wine/win firefox runs like a dog. Just navigating to a page takes forever, which is why I'd like to get the plugin thing working so it only starts up when I actually need it.

---

### Post by glennric on 2006-06-20
You probably have to make a link in /opt/firefox/plugins to /usr/lib/mozilla-firefox/plugins/mozplugger.so.  To do this type:
sudo ln -s /usr/lib/mozilla-firefox/plugins/mozplugger.so /opt/firefox/plugins/
This assumes you have firefox installed in /opt/firefox

---

