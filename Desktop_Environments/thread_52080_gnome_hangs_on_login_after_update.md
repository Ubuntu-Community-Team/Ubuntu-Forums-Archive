---
title: "gnome hangs on login after update"
date: 2005-07-26
forum: Desktop Environments
---

### Post by eriktown on 2005-07-26
Some packages were offered for update yesterday -- I don't remember which ones; there were about a dozen -- and after updating, I haven't been able to log into a gnome session successfully either in failsafe mode or regular mode. X *does* start, and I *do* get the gdm login screen as expected -- but once I enter my username and password, the window manager never starts -- I just get a blank screen with a white arrow mouse cursor.

I'm able to get to a console with Ctrl-Alt-F1, but I can't seem to restart the daemons (gnome-restart doesn't seem to exist). I also can't find where information on the problem might be logged.  Does anyone know how I can fix this, or at least find a log that might have some useful error messages?

---

### Post by crouton on 2005-07-26
[QUOTE=eriktown]Some packages were offered for update yesterday -- I don't remember which ones; there were about a dozen -- and after updating, I haven't been able to log into a gnome session successfully either in failsafe mode or regular mode. X *does* start, and I *do* get the gdm login screen as expected -- but once I enter my username and password, the window manager never starts -- I just get a blank screen with a white arrow mouse cursor.

I'm able to get to a console with Ctrl-Alt-F1, but I can't seem to restart the daemons (gnome-restart doesn't seem to exist). I also can't find where information on the problem might be logged.  Does anyone know how I can fix this, or at least find a log that might have some useful error messages?[/QUOTE]
 I believe it's /var/log/Xorg-error.log.  Somewhere in the /var/log directory for sure.

Have you tried the 'safe mode' login option?

---

### Post by eriktown on 2005-07-26
[QUOTE=crouton]I believe it's /var/log/Xorg-error.log.  Somewhere in the /var/log directory for sure.

Have you tried the 'safe mode' login option?[/QUOTE]

I have; it behaved in the same fashion.

Spookily enough, I installed WindowMaker (which is my normal wm of choice anyhow) and was able to use it successfully... but I forgot to make it my default window manager, so the next time I logged in, gnome tried to start -- and succeeded! It's lost all my preferences, but it seems to be working again. *shrugs* 

Either way, I'm going back to Windowmaker; I'd forgotten what a nice, light memory footprint it had, and I really use windowmanagers to herd terminal windows with anyhow.

---

