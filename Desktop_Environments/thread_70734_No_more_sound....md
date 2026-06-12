---
title: "No more sound..."
date: 2005-10-01
forum: Desktop Environments
---

### Post by SilverTab on 2005-10-01
I use the AC' 97 codecs in gnome and everything is fine, but as soon as I install a KDE app on gnome (ex: Kopete or Amarok) I get a sound driver error when I open it, and from there, no more sound...

(note sure what the error message is...something about the sound driver that cant be found, or that is busy....I only get it the first time I open an app that require sound driver, on a fresh reboot...from there...every sound output goes to /dev/null)

Ill try to reboot and get the exact message again....in the meantime...any help would be appreciated :confused: 

(Note: Its the second time I install ubuntu and I still get the exact same problem)

---

### Post by SilverTab on 2005-10-01
Also: Right now if I try to play an mp3 in Rythmbox I get:
"Could not open resource for writing"

I click OK...and then
"Could not pause playback"


everything was running fine before I installed Amarok and Kopete

---

### Post by SilverTab on 2005-10-01
Update:
I now have sound in Amarok...what fixed it for me was:
```

apt-get install amarok-xine

```


So now:
Amarok sound is working...but all the other app still dont have sound (rythmbox, kopete, gaim...in other words...EVERY other app...)

---

### Post by psychicdragon on 2005-10-01
esd is probably dead. You can start it back up by typing esd & in a terminal.
Or, you can stop using esd. Run gstreamer-properties and change the output audio sink from esd to alsa.

---

### Post by SilverTab on 2005-10-01
mmm I get this when I type esd in a terminal:

esd: Esound sound daemon already running or stale UNIX socket


BUT I think i'm starting to narrow down the problem: I rebooted...
Everything was fine...sound was working in both Rythmbox AND amarok so apparently installing amarok-xine fixed that...

now: I opened kopete...and from there I got an error saying:
"Error while initializing the sound driver...
...
...
will keep using dev/null"


and then...no more sound in amarok or rythmbox SO apparently..as soon as I run a KDE app, my sound stop working....I guess using amarok with xine fixed that...but I still have the same problem with kopete since its a kde app...

---

### Post by psychicdragon on 2005-10-01
If you're running both kde and gnome apps esd is probably going to get dead a lot. It doesn't start with a kde session either. Esd will only work well for you if you're only using gstreamer based applications in the gnome environment.

I would really recommend that you switch the gstreamer backend to alsa as I mentioned in the other post.

---

### Post by SilverTab on 2005-10-01
ok I did what you said...

now I got sound in Gnome (menu sounds etc...)...but not in amarok...
and in Rythmbox I get an error saying "ALSA device "default" is already in use by another program."

---

### Post by SilverTab on 2005-10-01
Problem Fixed:
Solution: This thread [http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

psychicdragon: thanks for your help...using ALSA was indeed part of the solution...problem apparently is that I couldnt hear multiple sounds (from both ESD and ALSA) at once...and this thread explained how to do it :)

the big problem apparently is my cheap on-board sound cart...that doesnt support hardware mixing

---

