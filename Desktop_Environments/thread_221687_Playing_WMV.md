---
title: "Playing WMV"
date: 2006-07-23
forum: Desktop Environments
---

### Post by slugkilla on 2006-07-23
Hi. I am wanting to play the WMV format in either Xine or Mplayer. I followed the part in the Ubuntu guide.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

But for some reason I still can not play this format. The file I'm trying to play is the first 24 episode that The Burger King is giving away for [free]("http://profile.myspace.com/index.cfm?fuseaction=user.viewprofile&friendid=78733550&MyToken=93e3ca1a-8443-4ada-afe5-64cd2ca792c7") Can someone help me? Thanks

---

### Post by xXx 0wn3d xXx on 2006-07-23
Use [ Automatix ](http://ubuntuforums.org/showthread.php?t=177646) and install the audio and video codecs.

---

### Post by slugkilla on 2006-07-23
Thanks for the help. I installed Automatix and from there installed the dvd nonfree codecs and the mulitmedia audio video codecs. WMV still does not work right. All that happens is colors and blury shapes move on the screen and then and window pops up saying that there are too many video packets are in the buffer. Why does this happen? Do I need to install more codecs?

---

### Post by ardchoille on 2006-07-23
If it is a wmv9 video, you won't be able to watch it becuase the codecs don't support wmv9.

---

### Post by slugkilla on 2006-07-23
oh :( But anything older than that should work?

Edit: I just tested it on some other things and they worked. Even one that said it was WMV9. I Guess this one is just encripted or too new or something.

---

### Post by Hi-Teck on 2006-07-23
Try:

Add this line to you /etc/apt/sources.list
"deb [http://download.gna.org/praksys](http://download.gna.org/praksys) praksys/"

Then go into synaptic and install "w32codecs"

No quotes

---

