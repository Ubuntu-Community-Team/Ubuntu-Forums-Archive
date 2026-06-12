---
title: "Xubuntu 20.04 desktop icons disappear"
date: 2020-10-07
forum: Desktop Environments
---

### Post by lou6 on 2020-10-07
I recently installed Xubuntu 20.04.1 from dvd.  Ran well for a day, then on login Xubuntu loaded with desktop icons but no panel at the top of the screen.  Restarted and then had  the top panel but no desktop icons.  Subsequent boots continued with top panel but no desktop.  Since the system was unusable in this state I reinstalled Xubuntu 18.04 which works (as always) perfectly.

Has anyone else had similar problems with install from dvd?  Our other machine was upgraded to 20.04 (rather than installed from dvd) and is running okay.

---

### Post by CelticWarrior on 2020-10-07
There should be no different in the resulting installation from any properly done installation media. However, reading about DVDs for that purpose in 2020 feels like time travel to a distant past.

Whatever happened - now impossible to know/troubleshoot - wasn't related in any way with the installation media.

---

### Post by lou6 on 2020-10-07
Is there an advantage to burning installation media to usb instead of dvd?  I only use dvd from long habit/experience...

I don't know how to begin troubleshooting an Xubuntu home page with no desktop icons and only the top panel - I posted about it here to ask people who know better than I.

---

### Post by ajgreeny on 2020-10-07
If it matters to you the USB live system will always boot and install faster than DVD; in the long run, however, it really doesn't matter which you use as it will be used only the once, ie, to install the full system.

Like CW, I haven't used an optical disk on my computer for a long time except to rip either DVD to video file or audio-CD to audio file.

As for your icons/panel problem, try renaming the ~/.config/xfce4 folder as a backup with your xfce desktop not running by logging out, using Ctrl+Alt+F2 to get to a command line, login with username and password (password will not show on screen) then run command ```
mv .config/xfce4 .config/xfce4-backup
```
Now Ctrl+Alt+F7 to get back to a GUI and with luck you may get the desktop you want, though you may need to restore icons and panel applets if you added lots to your system.

---

### Post by lou6 on 2020-10-07
ajgreeny; Thanks for your reply.  I did not know that it was possible to gain access to my OS by that method.  I'll keep a link to this post in case anything like this ever happens again.

---

