---
title: "Logging off  &amp; desktop"
date: 2009-05-26
forum: General Help
---

### Post by adzik on 2009-05-26
So I have an issue with logging off (graphically).
This doesn't occur if I choose to only function via the shell.
Once I am logged on and working away, if I then go to log off through gnome gui (or full shutdown sometimes), it will look like it's going down, and just as soon as gnome disappears, I get a black screen (blank active) and it stalls there and does not go back to GDM login or continue shutting down with any messages. This happens every time when logging off, and part of the time when performing a full shutdown.
The other issue that involves the desktop is 1 out of 2 times when I login, the desktop does not bring up any icons or files I have set there. They are all in fact there, because when I check under Desktop/ in the terminal, it's all good. So the issue here is what should I check and do to fix this as well?

I am determined to learn a bit more about fixing the issues rather than the cheap 'n' easy reinstall.
I am using 8.04.

---

### Post by KhurramM on 2009-05-26
I had the first of your issues, on my hardy.

I found that by installing root and swap on primary partitions removed my error.

For the second one, your window manager isnt running.

use

$ metacity

wait till it show s up.

I hope u get your issues resolved.

---

### Post by soro2005 on 2009-05-26
As for the shutdown: That sounds like a power management thing. You could try to find out whether other people have had the issue with your computer model.

As for the second issue: That's not about metacity, it's that nautilus either crashes, or doesn't even try to start up. You could quote here the contents of the file ~/.xsession-errors

---

### Post by adzik on 2009-05-26
I'll clarify the second issue a bit better.  GDM login comes up, I login, gnome gets going and everything is there regarding the gui, except all the files and active icons on the desktop do not appear. Just the wallpaper and that's all.

And here is the output of the .xsessions-errors:

> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/AKDPC:/tmp/.ICE-unix/5344
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Window manager warning: Failed to read saved session file /home/akdm/.metacity/sessions/default0.ms: Failed to open file '/home/akdm/.metacity/sessions/default0.ms': No such file or directory
seahorse nautilus module initialized
Initializing nautilus-share extension
11

** (nautilus:5439): WARNING **: Unable to add monitor: Not supported
Using /home/akdm/.wbar config file.
Using a Super Bar.
  PID TTY          TIME CMD
 5408 ?        00:00:00 pulseaudio
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

---

### Post by soro2005 on 2009-05-26
Does the Wbar work? When you don't see the icons, can you post the output of
```
ps aux | grep nautilus
```
Also, can you move all your files, including the hidden ones, off of the Desktop, and perhaps only leave a simple text file for control? Then try again whether that solves the issue? Sometimes, nautilus tries to produce a thumbnail of a corrupted file and crashes.

---

### Post by adzik on 2009-05-28
Yes, the Wbar works fine.

Output of ps aux | grep nautilus:
```
akdm      5437  0.0  1.4 219556 27348 ?        S    09:15   0:06 nautilus --no-default-window --sm-client-id default2
akdm      5847  0.0  0.0   3008   756 pts/0    R+   11:05   0:00 grep nautilus
```

I've also moved all the files off the desktop completely. Same issue just occurred on latest reboot.

---

