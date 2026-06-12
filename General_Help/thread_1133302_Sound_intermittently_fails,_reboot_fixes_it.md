---
title: "Sound intermittently fails, reboot fixes it"
date: 2009-04-22
forum: General Help
---

### Post by edmicman on 2009-04-22
Running 8.10 on a Dell Inspiron 600m for quite awhile now, and love it.  However, I do have one sound-related problem.  Every once in awhile, my sound system will just crash, and stop working.  Usually it's after a Flash/Firefox related crash or some sort.  But after that, sounds no longer work.  The mute button works, but no matter what, no sound at all.  A reboot fixes everything and it works as normal.

I'm wondering if there's a way to "reboot" just the sound system?  In Windows, I'd look at the Device Manager, assuming to see something about the device not working.  I'd disable/enable it and it would probably get back working.  I guess finding/fixing the underlying problem would be good, too, but I imagine it's probably related to Adobe's Flash somehow.  So just a quick way to reset the sound system rather than having to reboot the entire computer would be a decent start.  Any ideas?  Thanks!

---

### Post by DagMan on 2009-04-23
you can try killing pulseaudio and restarting it.  I *think* it runs on a per-user basis in intrepid but I'm not sure.  You'de want to 
```
killall pulseaudio
pulseaudio
```You might look to see if flash was still running and kill it first if it was.  You might also want to look that you're running the most recent flash and that flashplugin-nonfree-extrasound and libflashsupport are not installed.  See here [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)


Don't know if this helps.  Good luck.

---

