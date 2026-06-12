---
title: "clock date format in Karmic"
date: 2010-01-20
forum: Desktop Environments
---

### Post by DougZ on 2010-01-20
Okay, this is driving me nuts.  I absolutely detest the default date/time format.  Usually one of the first things I do is change this.

I've found multiple references to changing the behaviour with gconf-editor and changing the values (which do not exist in Karmic).

They do exist under /schemas/apps/clock_applet/prefs/custom_format but this cannot be changed as it is a schema?

---

### Post by stinkeye on 2010-01-20
See this thread:
[_**[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?p=8629954#post8629954[/COLOR]**_]("http://ubuntuforums.org/showthread.php?p=8629954#post8629954")

---

### Post by DougZ on 2010-01-20
Many thanks.  It turns out my problem was that I blindly use sudo to launch any command that makes configuration changes.

If you launch gconf-editor using sudo the key does not exist!  This is what was throwing me.

Launching gconf-editor as myself and voila the required keys exist.

---

### Post by kenkaku on 2010-04-08
Awesome.
Thanks. 
I was having the same sudo problem. :-/
Also, since I have removed the clock and added it back, the path I had to go to in gconf-editor was:
apps/panel/applets/applet_1/prefs.

But once I was there, it was all gravy. 
No need to reboot. The changes happened in real time. 
It looks like you can even use HTML notation. I bolded mine using "<b>....</b>".
I got that idea from here:
[http://tips4linux.com/custom-clock-in-gnome/](http://tips4linux.com/custom-clock-in-gnome/)

---

