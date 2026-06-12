---
title: "Can't play .asx files"
date: 2006-06-03
forum: Desktop Environments
---

### Post by calande on 2006-06-03
Are you able to play this file? [http://di.fm/wma/chillout.asx](http://di.fm/wma/chillout.asx)
Neither Totem nor Rhythmbox can play it. I always get an error:

Unable to open destination, maybe you don't have file permission

I have the codecs installed ; I can read MP3 files without problems.
Thanks,

---

### Post by Antman on 2006-06-03
[QUOTE=calande]Are you able to play this file? [http://di.fm/wma/chillout.asx](http://di.fm/wma/chillout.asx)
Neither Totem nor Rhythmbox can play it. I always get an error:

Unable to open destination, maybe you don't have file permission

I have the codecs installed ; I can read MP3 files without problems.
Thanks,[/QUOTE]

The .ASX audio file is playing for me. I use mplayer in Firefox with current codecs.
See Wiki for details: [Wiki]("http://help.ubuntu.com/6.06/ubuntu/desktopguide/C/internet.html")

---

### Post by calande on 2006-06-03
Thank you, actually I'm unable to find mozilla-mplayer...

---

### Post by meng on 2006-06-03
Have you got multiverse enabled?

I have never previously had luck getting Rhythmbox or Totem to play .asx streams. And I tried again just now, things haven't changed with the upgrade.

I used to use xine to play these (totem-xine didn't work, go figure). Mplayer plugin (v3.05 I think) didn't work then either. But the current version in the dapper multiverse works great!!!

Thanks for raising this issue, else I never would have realized it.

---

### Post by Antman on 2006-06-03
[QUOTE=calande]Thank you, actually I'm unable to find mozilla-mplayer...[/QUOTE]

Be sure to enable the **Multiverse** repository.

---

### Post by calande on 2006-06-04
[QUOTE=Antman]Be sure to enable the **Multiverse** repository.[/QUOTE]

Yes, I have multiverse enabled, but mplayer plugin doesn't show up ](*,)

---

### Post by calande on 2006-06-04
Ok, for some reason now it is working :)
It seems that something updated or rebuilt my list of packages (No idea what), and mozilla-mplayer appeared in the list, I installed it and I am listening to Digitally Imported as I'm writing :)

Is there a way to update the package list using the terminal or Synaptic?
Thanks a bunch!

---

### Post by calande on 2006-06-04
One more problem, I have no video on this page, only sound using mozilla-mplayer plugin and Firefox: [http://jt.france2.fr/20h/](http://jt.france2.fr/20h/)
Any idea to have video too?

---

### Post by Antman on 2006-06-04
[QUOTE=calande]One more problem, I have no video on this page, only sound using mozilla-mplayer plugin and Firefox: [http://jt.france2.fr/20h/](http://jt.france2.fr/20h/)
Any idea to have video too?[/QUOTE]

It's working for me. You probably need to Install the W32 codecs. Check the Wiki for Restricted formats.

---

### Post by calande on 2006-06-04
:( I installed them this afternoon...

---

