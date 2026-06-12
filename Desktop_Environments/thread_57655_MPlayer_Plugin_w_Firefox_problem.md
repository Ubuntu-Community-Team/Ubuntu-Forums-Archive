---
title: "MPlayer Plugin w/ Firefox problem"
date: 2005-08-17
forum: Desktop Environments
---

### Post by mtelewicz on 2005-08-17
Hello all!  I've searched all over for an answer to this problem, but I just can't find it.  I'm hoping someone here might be able to help.

I've installed the MPlayer plugin (and MPlayer itself) for use in Firefox.  All of these packages were installed via Synaptic.  The plugin seems to work rather well except for Quicktime movies using the SVQ3 codec.  Now, MPlayer itself seems to be able to play these movies just fine.  The plugin, however, displays no video and plays some choppy, looping audio of the first few seconds of the movie, then stops altogether.

Here's some version information:
MPlayer 1.0pre6-3.3.5
MPlayerplug-in v2.70
Firefox v1.0.6

I should also mention that I've installed the w32codecs package and that these videos are working in xine as well.  I've tried getting other plugins to work such as mozplugger, but I've had the most success with MPlayer.

Thanks!

---

### Post by kamiccolo on 2005-08-17
Then you have the same problem like me. Your mplayer plays Quicktime-movies because of the w32codecs. The browser-plugin doesn't seem to use these codecs. Like you I have installed the same mplayer and the same plugin. I also have the same version of Firefox. My plugin also doesn't work properly.
I have installed the Media Connectivity Extension for Firefox, but that doesn't fix the problem.

---

### Post by mtelewicz on 2005-08-17
Hmm...well, it is good to know I'm not alone in this, but I'm also sorry to hear that you're having problems as well.  I might try installing the latest versions of MPlayer and the plugin; I know that the plugin, at least, is quite a bit old.

---

### Post by mrguytx on 2005-08-17
use the totem-xine plugin, there are instructions on this forum somewhere that I followed and it worked great.

---

### Post by mtelewicz on 2005-08-17
I tried the totem-xine w/ mozplugger instructions, and I had no luck whatsoever.  That may be due to the fact that I'm running all this in a 32-bit chroot (running amd64).

I don't know.  I may give that another go.  But I couldn't get anything to play using that, and I can get mostly everything to play with the mplayerplug-in.

---

### Post by kris kincaid on 2005-08-17
I have found the MediaPlayerConnectivity Firefox plugin is really handy to have. It allows you to select various players for various filetypes. It may help you out :-? 

[http://membres.lycos.fr/sethnakht/](http://membres.lycos.fr/sethnakht/)

---

### Post by mtelewicz on 2005-08-17
Thanks for that.  I'll have to check out that plugin.

I also just wanted to add that upgrading to mplayerplug-in 3.05 didn't fix the issue, although now I have controls!  Also, I tried using the regular Mozilla browser, and I'm seeing the same thing.

---

### Post by kamiccolo on 2005-08-18
I have already installed the Firefox extension, but I don't know how to find out which application I should use. The Programm which can play everything is totem which uses xine. When I use /usr/bin/xine als app, then I hear nothing. /usr/bin/totem also doesn't fix this problem. What can I do?

---

### Post by kamiccolo on 2005-08-20
*pushing upwards*

---

