---
title: "sound and gnome-settings-daemon problems"
date: 2006-09-28
forum: Desktop Environments
---

### Post by kashms on 2006-09-28
After a file system crash (reiserfs) and recovery I'm having trouble with system sound and gnome-settings-daemon. The system sound has stopped working (e.g. no login or logout sounds). Alsamixer gives a segmentation fault as does trying to start the gnome-setting-daemon in a terminal. When I login I get the following error from gnome-panel:

"The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet". Do you want to delete the applet from your configuration?"

and from gnome-settings-daemon:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

The last error message was:

System exception: IDL:Bonobo/GeneralError:1.0 : Child process did not give an error message, unknown failure occurred

GNOME will still try to restart the Settings Daemon next time you log in."

I'm then stuck with a boring gtk theme, which I can't change. I suspect there is something wrong in a sound related package but which? I can play music, movies and play games with sound fine. It is just the system sound.

P.s. When I start gnome-control-center in a terminal it gives an output in terminal: "ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) -diagrammer". And there is no sound card listed in sound preferences.

---

### Post by Plexi on 2006-10-09
I had the same problem.

Fix:

Alt+F2 (Will bring up the RUN Application)

Type "gnome-settings-daemon"

Press Run

This should fix it

Good Luck!

---

