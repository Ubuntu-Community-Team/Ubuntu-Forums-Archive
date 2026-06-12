---
title: "KDE sound notifications not working in Gnome"
date: 2008-08-07
forum: Desktop Environments
---

### Post by retrovertigo on 2008-08-07
Specifically when using Amarok, when I delete a podcast or do anything else that will generate a pop-up dialog and sound effect, the sound does not play.  I am using Gnome Desktop on Ubuntu 8.04.  Both Amarok and Gnome are set to use ALSA for sound.  Music plays just fine in Amarok, it's just the sound events/notifications that aren't working.  Does anyone know how to resolve this?

---

### Post by evets25 on 2008-08-07
Don't use amarok with gnome? No seriously, amarok has a GTK+ equivalent called exaile, you could give it a try. The problem, I suspect, is that Amarok expects the KDE sound system to be in place (arts) and tries to use it for notifications and whatnot, even if it is set to play music through ALSA directly. Of course in gnome, arts simply isn't there, they have their own sound system for notifications, so when Amarok sends the signal to arts to play a sound, it gets lost in the void...

---

### Post by retrovertigo on 2008-08-07
> **evets25 said:**
> Don't use amarok with gnome? No seriously, amarok has a GTK+ equivalent called exaile, you could give it a try. The problem, I suspect, is that Amarok expects the KDE sound system to be in place (arts) and tries to use it for notifications and whatnot, even if it is set to play music through ALSA directly. Of course in gnome, arts simply isn't there, they have their own sound system for notifications, so when Amarok sends the signal to arts to play a sound, it gets lost in the void...

aRts is installed and appears to be running:

```
mercury@shadow:~$ ps aux | grep arts
mercury   6407  0.0  0.2  93464  7840 ?        S    Aug06   0:13 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -l 3 -f
```

I'm not familiar with aRts per se, maybe there's something else that needs to be done in order to get it to pick up the notifications?

---

### Post by retrovertigo on 2008-08-27
Been looking more into this and haven't found a solution.  I can't be the only one with this problem, has anyone else seen this?

---

### Post by retrovertigo on 2008-08-28
I am using PulseAudio as my sound server in Gnome, might it be that artsd can't access the sound card because it's being used by PulseAudio?  If so, is there a way that KNotify can be configured to use PulseAudio rather than aRts?

---

### Post by retrovertigo on 2008-09-08
OK, I figured it out.  I'm not sure if this will work from a fresh install of Ubuntu (that is to say, I may have installed a needed library during the course of my troubleshooting), but this is what ended up working.

1) First, make sure that you are using PulseAudio sound server in System -> Preferences -> Sound.
2) Next, install KDE Control Center (**sudo apt-get install kcontrol**)
3) Run KDE Control Center (either by running **kcontrol** from the command line, or hitting Alt+F2 and typing **kcontrol**).
4) Under "Sound & Multimedia", select "Sound System"
5) Click the "Hardware" tab.
6) Where it says "Select the audio device", choose "Enlightened Sound Daemon".
7) Click "Apply".

You can then click on "System Notifications" on the left and select an event with a sound notification set for it, and use the Play button next to where it says "Play a sound" to test and make sure that the sound plays.


I've found that the KDE notifications play a little loud, so while on the "System Notifications" screen, you can click the "Player Settings" button in the lower right and reduce the volume there.

---

