---
title: "Changed from Unity to gnome, after reboot unable to login"
date: 2016-09-08
forum: Desktop Environments
---

### Post by docdoc2 on 2016-09-08
Hey ho,

i followed this thread [https://askubuntu.com/questions/450294/how-to-switch-from-unity-to-gnome](https://askubuntu.com/questions/450294/how-to-switch-from-unity-to-gnome)

and just used 
> sudo apt-get install gnome-session-flashback

Gnome worked fine, i could could use the metacity and compiz version.

 i also changed something with unity by using
> sudo apt-get remove --purge unity-lens-[lensName]
in order to make the first splash quicker (after each reboot it took the splash ~1min to load!)

But now when the login screen appears, i hear a different sound than the usual drums and when try to login, no matter if i try unity, gnome or awesome, i am directly sent back to the login screen. The guest session works thought.

Should i just uninstall the gnome? How can i login again?

---

### Post by docdoc2 on 2016-09-11
is there nothing i can do? i want to use my computer again

---

### Post by GXdmWQH on 2016-09-11
> **docdoc2 said:**
> is there nothing i can do? i want to use my computer again

You could check some log files by hopping over to a TTY - at the login screen (or once the kernel has loaded) press ctrl + alt + F1/F2/F3/F4/F5/F6 - each of these represents a TTY which you can use to access your file system and manage drivers etc. Press ctrl + alt + F7 to return to the desktop environment. My recommendation would be to update your packages and see if you get dependancy issues. Alternatively, on the login screen click the cog wheel and try the other desktop environments, as they may still work.

---

### Post by docdoc2 on 2016-09-11
Sorry, i did soemthing else, too. i used a command as root/sudo: startx. i think that was the problem! checking now for other solutions...

---

### Post by docdoc2 on 2016-09-12
So, gnome installation had nothing to do with it, you can delete this one.

---

