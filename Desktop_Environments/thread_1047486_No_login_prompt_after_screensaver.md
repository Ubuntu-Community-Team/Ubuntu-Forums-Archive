---
title: "No login prompt after screensaver"
date: 2009-01-22
forum: Desktop Environments
---

### Post by whiskeylover on 2009-01-22
Hi,

I'm a relative n00b to linux. I bought a used desktop a week ago and installed Ubuntu 8.10 on it alongside of XP. 

If I leave it logged it, after a while it starts the screensaver and the display shuts down. On moving the mouse, the display comes back up and screensaver shuts down as expected. The only problem is that all I see on the screen is the background wallpaper and the mouse pointer and nothing else.

There is no taskbar, no menubar, no login prompt either. I can't log back into it by any means. I have to SSH into it from another computer and reboot it. 

This has happened everything the computer is left idle till the display shuts down.

Can someone tell me if there is known solution to this problem? Or am I forced to abandon it and go back to XP :confused:

TIA
-whiskeylover

---

### Post by XanTrax on 2009-01-22
> **whiskeylover said:**
> Hi,

I'm a relative n00b to linux. I bought a used desktop a week ago and installed Ubuntu 8.10 on it alongside of XP. 

If I leave it logged it, after a while it starts the screensaver and the display shuts down. On moving the mouse, the display comes back up and screensaver shuts down as expected. The only problem is that all I see on the screen is the background wallpaper and the mouse pointer and nothing else.

There is no taskbar, no menubar, no login prompt either. I can't log back into it by any means. I have to SSH into it from another computer and reboot it. 

This has happened everything the computer is left idle till the display shuts down.

Can someone tell me if there is known solution to this problem? Or am I forced to abandon it and go back to XP :confused:

TIA
-whiskeylover

Run top or "ps -A | more" and see if gnome or gdm process is running.  You can either SSH in or press ctrl+alt+f1 to open a terminal.  You could also press ctrl+alt+f7 and see if it appears after that.  Also, try ctrl+alt+backspace to restart gdm/gnome and appear back at the login screen.  Let me know if ctrl+alt+backspace works.  If it works, then you wont have to restart but at least you have something to go on.

---

### Post by whiskeylover on 2009-01-22
None of those key combinations work. I cant get a terminal by pressing Ctrl-Alt-F1. I can't restart gdm either and can't get the login screen. Ctrl-Alt-Backspace doesn't work either.

But the desktop wallpaper is visible and the mouse pointer. But thats it.

---

### Post by amac777 on 2009-01-23
Perhaps try changing to a different (simple) screen saver. (Maybe the one you have now is corrupting things somehow?)

just an idea to see if that is the problem.

---

### Post by whiskeylover on 2009-01-23
I'm using the green Matrix screen saver. I'll change it to a blank one to see if the SS was the problem.

---

### Post by XanTrax on 2009-01-23
If the SS is not the problem can you please look at the caps lock LED on your keyboard and tell me if it is blinking?  If it is, it could be a kernel panic but I don't think it would be that. It'd be nice to rule it out though :p.

---

### Post by whiskeylover on 2009-01-23
I just left the computer idle for some time. Also changed the SS to blank. I'll check it after half an hour or so. (Usually this problem doesn't happen if I kill the screen saver within a few mins.)

XanTrax, the Caps lock doesn't blink :)

---

### Post by XanTrax on 2009-01-23
> **whiskeylover said:**
> I just left the computer idle for some time. Also changed the SS to blank. I'll check it after half an hour or so. (Usually this problem doesn't happen if I kill the screen saver within a few mins.)

XanTrax, the Caps lock doesn't blink :)

I figured it wouldnt be :p.  I have had some similiar problems with some screensavers before so it might just be that screensaver.

---

### Post by whiskeylover on 2009-01-23
The blank SS doesn't seem to have this problem. I'm so happy. I'll keep an eye on it and see if it has the same problem after I wake up tomorrow morning. 

Thanks for you help guys.

---

