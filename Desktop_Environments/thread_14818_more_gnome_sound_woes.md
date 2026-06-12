---
title: "more gnome sound woes"
date: 2005-02-10
forum: Desktop Environments
---

### Post by Bionic Bunny on 2005-02-10
I know this has been addressed before, but I have no sound at all.  My volume control is stuck all the way down, and when I try to open the volume control from the applications menu, it says "sorry. no mixer elements and/or devices found".  Now, the sound worked when I first instlled, but it disappeared somewhere down the road.  I have gstreamer installed, and I have tried installing alsa to remedy the problem, but to no avail.  Any ideas?  Thanks

---

### Post by Xian on 2005-02-10
I'm not sure what version of gstreamer you are using (adjust as needed), but you can try a command like:
```
$ gst-register-0.8
```

---

### Post by Bionic Bunny on 2005-02-10
Thanks for the info, I'll remember that for future issues.  It seems that the sound is still not working, however.  Might I also add that I've updated my kernel to the 686 kernel...Would that have anything to do with it at all?

---

### Post by ikletti on 2005-02-10
[QUOTE=Bionic Bunny]Might I also add that I've updated my kernel to the 686 kernel...Would that have anything to do with it at all?[/QUOTE]
As far as I can tell: No. I've had working sound with the 386 kernel and have sound now that my system is running the 686 kernel (the module is snd_intel_8x0).

Ingo.

---

### Post by alastair on 2005-02-10
See if alsa see your sound card :

cat /proc/asound/cards

Check your sound module is loaded : lsmod

Check the system logs to see if there is anything odd happening :

/var/log/dmesg
/var/log/syslog

---

### Post by alastair on 2005-02-10
On another thread - might be worth trying :

sudo /etc/init.d/alsa force-reload

[http://ubuntuforums.org/showthread.php?t=14890](http://ubuntuforums.org/showthread.php?t=14890)

Check the logs.

---

### Post by Bionic Bunny on 2005-02-10
[QUOTE=alastair]See if alsa see your sound card :

cat /proc/asound/cards

Check your sound module is loaded : lsmod

Check the system logs to see if there is anything odd happening :

/var/log/dmesg
/var/log/syslog[/QUOTE]

Eeep!  It doesn't see my sound card.  Now, I'm a total n00b, so....how might i go about resolving this?  Btw, it's not anything new or spiffy, just a soundblaster live! 5.1

*EDIT*
Well guys, looks like it's time to let this thread die.  Turns out it was hardware.  I booted into windows, because i had a suspicion that it was, and well...turns out i was right.  Good thing i had a spare card laying around.  Thanks for all the help, guys!

---

