---
title: "Broken icons in start panel"
date: 2006-09-02
forum: Desktop Environments
---

### Post by acorn22 on 2006-09-02
Today I was messing around with GRUB and some other stuff and was pretty close to loosing everything, but somehow fixed everything and all is now well.

Actualy all is not well. See now in my top panel, the Quanta, Mplayer and Firefox icons are broken. When I try to open Quanta or mplayer it says ```
Could not launch application

Details: Failed to execute child process "gmplayer" (No such file or directory)
```
Firefox works fine but the icon is broken. A while ago i ran a script i found in these forums to "fix" the FF icon, so I'll just re-run that (if i can find it) 

I'll have to re install Quanta and mplayer, but what i want to know is why did this happen? (or what could have caused it)

---

### Post by geektron on 2006-09-16
I have the same problem with my vmware icon. The icon dissapeared and I get the child process error. I already recompiled the app which usually fixes everything, but no luck. Any suggestions are appreciated.

---

### Post by skirkpatrick on 2006-09-16
It sounds like the icons do not have the correct command to start the application.  If you've reinstalled the application and it appears in the Applications menu, copy it back over to the top panel.  The other option is to right-click on the icon, go to properties, and fix the command manually.

---

