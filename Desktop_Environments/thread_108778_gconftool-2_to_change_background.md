---
title: "gconftool-2 to change background"
date: 2005-12-27
forum: Desktop Environments
---

### Post by LucidParody on 2005-12-27
hi, i'm using the following command to change the background:

gconftool-2 --type str --set /desktop/gnome/background/picture_filename /home/tom/media/pictures/wallpapers/planet.png

i notice it changes in the configuration editor but it doesn't change my desktop background.  do i have to do something to refersh the desktop or whatnot?

t.i.a.

---

### Post by Perfect Storm on 2005-12-27
-deleted
*nevermind*

---

### Post by LucidParody on 2005-12-27
any ideas? everywhere i search, it seems to give me that same answer for linux in general but is something different on ubuntu?

---

### Post by Perfect Storm on 2005-12-27
I'm not quiet sure what you want? Change desktop background? It's in the preferences tab.

---

### Post by LucidParody on 2005-12-27
[QUOTE=Artificial Intelligence]I'm not quiet sure what you want? Change desktop background? It's in the preferences tab.[/QUOTE]

I'm trying to change the background using the commandline (for scripting purposes).

---

### Post by art on 2005-12-27
have you tried "killall nautilus" after the gconftool thing? That should refresh desktop.

---

### Post by LucidParody on 2005-12-27
[QUOTE=art]have you tried "killall nautilus" after the gconftool thing? That should refresh desktop.[/QUOTE]

I want to set this script up as a cron job that runs every hour.  If I'm using nautilus and the script runs on the hour, won't that kill whatever I'm doing? Is there any way around this?

---

### Post by art on 2005-12-27
the killall nautilus kills nautilus and starts it up again, so you'll have a new nautilus session.

---

### Post by art on 2005-12-27
Also look at this utilities, if the only job this script does is to change the background, then these might do the job.

[http://gnomefiles.org/search.php?search=wallpaper](http://gnomefiles.org/search.php?search=wallpaper)

---

### Post by Cordate on 2005-12-27
Poptone has come up with a Python script that'll change your wallpaer to a random image. You can read about it in [this thread.]("http://ubuntuforums.org/showthread.php?t=49336&") The last version, minus the last few commented lines, worked for me after I specified the directory for my images. 

If you want it to change the image at a regular interval (every day, every 12 hours, etc), you can do that by adding a line to your crontab that tells it to run the script at your preferred interval. There's more on that in the thread.

:) Have fun!

---

