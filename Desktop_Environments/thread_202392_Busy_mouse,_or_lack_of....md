---
title: "Busy mouse, or lack of..."
date: 2006-06-23
forum: Desktop Environments
---

### Post by maximinus_uk on 2006-06-23
Finally (!) I have converted my parents to Linux, and they are starting to love it (i.e. rock solid, faster than the old windows install etc...) but I have 1 minor snag to overcome.

I have placed a few icons on the desktop (since that's where they like them), but when you double-click one, the mouse icon does not change to a 'busy' cursor while the program is loading.

This may seem very minor, but the machine they are running on is a bit under-par on the memory front, and it can take something like K3B 10 or so seconds to start up (once it up, it's fine). What happens is my dad starts about 8 instances of the program because he can't tell if it's started yet.

I'm running Gnome/Dapper, tried google and these forums, but no obvious answer to this one. Anyone have any suggestions?

---

### Post by x64Jimbo on 2006-06-23
Use KDE, where the cursor bobs up and down? ;)

---

### Post by maximinus_uk on 2006-06-23
It's taken me enough time to convert them to Linux - letting them know that there is *more than one desktop gui* would kill them, I think!

---

### Post by ifokkema on 2006-06-23
Don't think you can change the cursor, but isn't there a mention of the program which is started on the window list?

---

### Post by maximinus_uk on 2006-06-23
There's no visual indication of the progran loading until its window opens up, at which point it also appears on the window list.

---

### Post by srt4play on 2006-06-23
Edit the desktop config file, and put 

StartupNotify=true

in it.

---

### Post by ifokkema on 2006-06-24
[QUOTE=srt4play]Edit the desktop config file, and put 

StartupNotify=true

in it.[/QUOTE]
Although I'm not having any problem, I'm always interested in learning. Could you tell me where the file you are referring to, resides on the system?

---

### Post by maximinus_uk on 2006-06-24
Excellent! But where exactly is the desktop config file? I couldn't find it in the obvious places, such as /.gnome or suchlike...

---

### Post by srt4play on 2006-06-24
:D 

By desktop config file, I mean the shortcut file you put on their desktop. 

In other words , from a terminal cd to the Desktop directory in their home directory. From there open up the shortcut file in nano and add the entry I mentioned above.

:D

---

