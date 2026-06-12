---
title: "America's Army help"
date: 2006-07-03
forum: Gaming &amp; Leisure
---

### Post by madddonkey255 on 2006-07-03
I recently installed America's army version 2.5 and when I try to run the armyops file in the folder I get the following error message in the terminal.> Cheat protection disabled
open /dev/[sound/]dsp: Device or resource busy
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error

Any help with this problem would be much appreciated.
Thanks,
Nolan

---

### Post by deathbyswiftwind on 2006-07-03
Do you know if your video card is setup right?

---

### Post by madddonkey255 on 2006-07-04
No, I'm a newbie.
Thanks,
Nolan

---

### Post by deathbyswiftwind on 2006-07-04
Alright then first what you need to do is get your video card installed. There are great threads in the forums for ati and nvidia cards so please look at the one you need. After you get your card setup your problem should disapear becuase glx is gl which is what you need to run AA

---

### Post by madddonkey255 on 2006-07-04
I just tried to install the glx and configure nvidia using this thread  [http://ubuntuforums.org/showthread.php?t=131267&highlight=xgl+nvida](http://ubuntuforums.org/showthread.php?t=131267&highlight=xgl+nvida), and now when I try running AA I get the following error message:> Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error

I've also used automatix to install the NVIDIA drivers before this.
Thanks for all your help,
Nolan

---

### Post by deathbyswiftwind on 2006-07-07
when you configured your settings did you make sure to check glx to load?

---

### Post by arnieboy on 2006-07-07
> **madddonkey255 said:**
> I just tried to install the glx and configure nvidia using this thread  [http://ubuntuforums.org/showthread.php?t=131267&highlight=xgl+nvida](http://ubuntuforums.org/showthread.php?t=131267&highlight=xgl+nvida), and now when I try running AA I get the following error message:
I've also used automatix to install the NVIDIA drivers before this.
Thanks for all your help,
Nolan

you need to enable "glx" in /etc/X11/xorg.conf
look for the phrase "#Load glx" in xorg.conf and replace it with "Load glx" (no hash in front). save exit and restart x-server or just reboot.

---

### Post by madddonkey255 on 2006-07-09
glx is set to load in xorg.conf.
Thanks,
Nolan

---

