---
title: "restore minimized applications with launchers"
date: 2010-07-17
forum: Desktop Environments
---

### Post by kfrancist on 2010-07-17
i'd like to be able to restore minimized applications by clicking on their launchers like you can do when you have awn or dockey installed.  but i'd rather not install awn or dockey since this is the only feature i want from them that the gnome panel doesn't already provide.

i found this thread:

[http://ubuntuforums.org/showthread.php?p=2356588](http://ubuntuforums.org/showthread.php?p=2356588)

which is from 2007.  apparently a small application, "launcher-restore",  was written to give program launchers the functionality i'm talking about--but that program is gone now--the attached deb file doesn't work at all.

so is there some other program that will do this now, a newer version of launcher-restore, or some even simpler way of setting things up the way i want them?

---

### Post by Linye on 2010-07-18
dockbarx has that behavior.

---

### Post by stinkeye on 2010-07-18
wmctrl allows you to do various window manager actions from the command line. 
A useful feature is "wmctrl -a <str>", which will switch to a window containing the string <str> in the title. 
For example, to activate a firefox window, and start firefox if there is no such window, use the following command as a launcher: 
```
wmctrl -a Firefox || firefox
```


To install wmctrl
```
sudo apt-get install wmctrl
```

I can't get the command to work from a launcher in the panel
but if you make a script and link to it in the launcher it works 
eg for firefox
```
#!/bin/bash
wmctrl -a Firefox || firefox
```

Then the command box in the launcher will look something like this
with the path to your script
```
sh /home/glen/startff
```
If you precede the path to your script with **sh** there is no need to make the script executable.

---

### Post by kfrancist on 2010-07-18
thanks to both of you!  these both seem like good options.  i'm sure one will suffice.  problem solved!

---

### Post by mujahied on 2010-07-18
hmmm good this even solved my problem thanks man

---

