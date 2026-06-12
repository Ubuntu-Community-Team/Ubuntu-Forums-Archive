---
title: "Dell Dimension 9100 problems"
date: 2007-06-30
forum: Dell  Ubuntu Support
---

### Post by radeon21 on 2007-06-30
So I installed Feisty and got everything set up the way I like it and then the theme suddenly reverted to an older theme randomly and then my keyboard started not working well in X and I couldn't launch the terminal.  By the keyboard not working I mean that if I try to type anything, the keys have weird bindings like opening up random applications, nautilus windows, etc.  So I thought it might have been time for a reboot.  I do, only to find that X will not launch (or GDM, I'm not really sure).  What happens is that I get to the point where I see the 'X' cursor and then it crashes.  It does this several times and then I get an error from X that says the display has crashed 6 times or so (no detailed output either, it usually does when there's a problem...) and then says it's going to wait 2 minutes to try again.  If I login from the console I can do a startx to get X going but the keyboard is still screwed up and everything is very unstable or won't launch (terminal still refuses to launch).

Needless to say, this frustrates me and I end up doing a full reinstall, and getting everything working again.  I shut my computer down before bed, get up and go to work/school, come back and start it back up only to have X tell me that it keeps crashing.  So I'm back to where I started.  Anybody have any ideas?  I successfully ran Dapper and Edgy on this machine without problems and I'm about to just hang it up and wait for Gutsy.  Help!

---

### Post by radeon21 on 2007-07-01
I guess it would help to mention that I've tried all installed kernels, I have a 7600GT (tried with vesa, nv, nvidia drivers) and everything is up-to-date.

---

### Post by khedron on 2007-07-01
What was the last change you did to the system before it became like this? 

Could you post the contents of your /var/log/xorg.log here, please?

---

### Post by radeon21 on 2007-07-02
The last change occurred a few reboots before it started happening and my log for X shows a clean start (which I guess is from just running startx).  I configured Beryl both times that Ubuntu died, but I've uninstalled it and restored my xorg.conf with no success.  The error that I get isn't from X I don't think, it just says that the display has crashed multiple times, waiting 2 minutes before trying to open a display on :0 or something like that.  The problem always starts when the last thing I can see in the boot stuff is 'running startup scripts something something rc.local'.  But, I've checked this and my startup script is empty, so I'm guessing it dies whenever it tries to do the next thing.

---

### Post by khedron on 2007-07-02
Okay - what's the output of 
```
sudo dmesg
```
You can put the output into a file by typing
```
sudo dmesg >/dmesg-output
```

---

