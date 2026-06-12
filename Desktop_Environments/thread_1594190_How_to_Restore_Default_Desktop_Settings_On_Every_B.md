---
title: "How to Restore Default Desktop Settings On Every Boot"
date: 2010-10-12
forum: Desktop Environments
---

### Post by steven_liauw on 2010-10-12
I maintain my school computers, with ubuntu installed on them.
The school children love Ubuntu, and as kids usually do, try funny and weird stuff on them.
So, they'll mess around with the panels, deleting them, adding new panels, deleting the menus, the windows application list, the logoff, putting weird wallpapers, etc.

I find myself constantly having to delete unnecessary new panels, adding back the Main Menu, etc.

So, how can I restore default desktop setting everytime I boot?
I thought about something like DeepFreeze, but that wouldn't do because I want them to be able to save files into the Home folder. I just want the desktop settings to stay constant.

I'm sure there is a way to do this. Maybe the gconf file? Maybe a script that runs on every boot?

If anyone has a script like that, or can show me the way to it, I'll really appreciate it!

PS: The computers are Ubuntu 10.10 and 10.04

---

### Post by ft-Orchard on 2010-10-12
Maybe the thread that I posted a few minutes ago will be the solution? 
This script backs-up all the panel settings. You can play around with it a bit more.

[http://ubuntuforums.org/showthread.php?t=1594187](http://ubuntuforums.org/showthread.php?t=1594187)

Press ALT+F2 and run "gconf-editor" Try to find settings that you should back-up. 
The panel settings: "apps > panel"
The desktop settings: "desktop > gnome" 

Then back them up as described in the thread.

---

### Post by steven_liauw on 2010-10-20
Thanks ft-orchard,

It's working perfectly!
I think that's one of the power of Ubuntu (Linux), it's so customizable.

---

