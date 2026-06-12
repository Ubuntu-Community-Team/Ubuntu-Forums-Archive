---
title: "Gdesklets, beryl don't start automatically"
date: 2006-11-24
forum: Desktop Environments
---

### Post by waltervalderrama on 2006-11-24
I 've already installed beryl with nvidia beta drivers. I runs ok, perfect. The problem is that I cannot make it run on gdm start. I go to preferences/system/sesions and add beryl-manager, but when I CTR+ALT+backspace and login again, nothing happens. I type beryl-manager in a terminal and beryl starts but i won't start when log in. What is the file I have to edit to do all this thing from a terminal???? 

The same way i cannot make gdesklets start when i log in

:-k :-k :-k :-k :-k :-k

---

### Post by canibal on 2006-12-08
i got the same problem with gdesklets. i add it to sessions --> start up and the next time i boot, it wont start, i check the start up and gdesklets isnt there.
any sugestings?

---

### Post by thelinuxguy on 2007-02-12
> **canibal said:**
> i check the start up and gdesklets isnt there.
The command is 
```
gdesklets start
``` and not just gdesklets.

@ waltervalderrama:
beryl-manager starts automatically on my system if I add it to System->Preferences->Sessions->Startup Programs. Since it remembers the last window manager used, its starts with Metacity (in my case). But beryl gets loaded and the icon appears in the tray.

However, I had trouble while enabling both beryl and gdesklets at startup. Both get loaded and appear in the 'Current Session' tab of Sessions but the gdesklets icon does not appear in the tray and the desklets don't show up on the desktop either. I have to start gdesklets manually from Applications -> Accessories. This happens only when Beryl is added to the startup as well. Otherwise gdesklets works fine at startup.

Let me know if you find anything more.

---

### Post by ic3man on 2007-02-18
i am using baryl and gdesklets come up but they are like minimized windows!
What can i do?

---

### Post by Austrian_Prototype on 2007-03-22
I had the same problem. After a while i simply deleted the desklets and added them again - annoying thing, but worked.

edit: sorry, didn't work! i just realized that some gdesklets are messed up and not handled like other desklets. e.g. FTP-CPU-plot. If I have some time, I'll correct that! 

I have the startup problem - beryl/gdesklets - too. I would appreciate any help!

edit: resolved this issue in the [session]start.sh:

#!/bin/sh
beryl-manager
sleep 4
gdesklets start
exec dbus-launch --exit-with-session gnome-session

thx in advance

---

