---
title: "Kmix Master and PCM settings (dcop stuff, too)"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Paradoxdruid on 2006-07-28
Recently, I've been playing at getting my Logitech MediaPlay mouse and it's buttons working correctly.  To do so, I've installed xbindkeys and changed my mouse protocol, following section 1 of the guide found here:  [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

This is working well, with a problem that's vexing me--  My computer's volume is controlled by the PCM slider in Kmix, and the "master" slider does nothing.

When called via dcop, I can set the volume of any of the sliders (i.e., to set the PCM volume to 70%, I use "[FONT="Fixedsys"]dcop kmix Mixer0 setVolume 1 70[/FONT]".  I can ALSO use "[FONT="Fixedsys"]dcop kmix Mixer0 increaseVolume 5[/FONT]" to move the master volume up in increments of 5%...  But my master volume does nothing.

Thus far, I have been unable to ascertain the command to increase the volume of the PCM channel.  increaseVolume does not appear to accept multiple arguments to specify which channel to use, or at least I don't know how to format it correctly.  

Does anyone know if Kmix can be set to increase the volume of the PCM channel?  Alternatively, is there a way to change my configuration so that the "Master" volume slider actually controls my system's volume?

Thanks in advance for any help.

---

### Post by Paradoxdruid on 2006-07-30
In case anyone else has this issue, I'll post the solution I came up with:

Instead of using dcop, I bound the following commands using xbindkeys:
```
#Volume High
"amixer sset PCM 10+ unmute"
    m:0x0 + b:13
    VolUp 

#Volume Low
"amixer sset PCM 10- unmute"
    m:0x0 + b:14
    VolDown 
```

Works like a charm.  I also bound the play/Pause key as follows:
```
#Pause Video
"/home/paradox/programs/playPause.sh"
    m:0x0 + b:17
    Pause 
```

where the script above looks to see if Kaffeine is running.  If it is, it toggles playpause in Kaffeine.  Otherwise, it toggles Amarok.  Here it is:
```
#!/bin/bash
#echo "`ps aux | grep kaffeine | grep -v grep | grep -v kio`"
if [ -n "`ps aux | grep kaffeine | grep -v grep | grep -v kio`" ]; then
	dcop kaffeine KaffeineIface pause
else
	dcop amarok player pause
fi
```

Enjoy!

---

