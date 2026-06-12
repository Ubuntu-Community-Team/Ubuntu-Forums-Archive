---
title: "Why do I need ESD??"
date: 2006-04-03
forum: Desktop Environments
---

### Post by bpont on 2006-04-03
Recently, I needed to uninstall Ubuntu's default Simple DirectMedia Layer package: **libsdl1.2debian-oss** and replace it with **libsdl1.2debian-all**, which includes sound drivers oss for esound, alsa, arts, and nas.  This allowed me to have sound for one of my fave games under Linux: *Armagetron*.

However, when I installed Audacity, it wouldn't load correctly or play or record sound unless I executed: ```
killall esd
``` then all worked fine.

So my question is, do I really need to have the Enlightenment Sound Daemon running at all?  And if not, how do I disable it from loading on startup?  Thanks!

---

### Post by Qrk on 2006-04-03
You only need esd if you like gnome sounds. I don't particually care for them, myself. You can disable them by System->Administration->Sounds.

When you restart Gnome, ESD should let you use your soundcard.

However, I haven't used Hoary in many months, so you may also want to remove the packages "esound" and "esound-common"

---

### Post by bpont on 2006-04-03
[QUOTE=Qrk]You only need esd if you like gnome sounds. I don't particually care for them, myself. You can disable them by System->Administration->Sounds.

When you restart Gnome, ESD should let you use your soundcard.

However, I haven't used Hoary in many months, so you may also want to remove the packages "esound" and "esound-common"[/QUOTE]

OK, Qrk, I followed your advice and indeed, doing so did disable system sounds and allowed me to hear and record sound using Audacity and even hear the sounds when playing Armagetron...HOWEVER, Rhythmbox does not work anymore.  If I try to play a song I get the following two dialog boxes:
[[IMG]http://img337.imageshack.us/img337/9728/error19se.png[/IMG]](http://imageshack.us)
[[IMG]http://img380.imageshack.us/img380/280/error2by.png[/IMG]](http://imageshack.us)

Also, I couldn't play music using XMMS until I changed the output plugin to ALSA, which I was only able to accomplish because I ditched the default Ubuntu Simple DirectMedia Layer package: **libsdl1.2debian-oss** and replaced it with **libsdl1.2debian-all,** which includes an alsa sound driver.

So how do I get Rhythmbox to work?  And why can't Ubuntu be configured to play system sounds, game sounds, music playing apps and a sound editor without so much tweaking and turning on/off of services?  Even ::cough:: Windoze seems better at this!  :-k

---

### Post by Qrk on 2006-04-03
Sound was always a problem in Hoary, but it was fixed in Breezy for the most part. (You may want to upgrade, unless there is something specific in Breezy that doesn't work for you)


Try:
```
sudo apt-get remove gstreamer-esd
sudo apt-get install gstreamer-alsa
``` 

If that doesn't work, you can find what is blocking your sound card with:

```
lsof /dev/dsp
```

---

