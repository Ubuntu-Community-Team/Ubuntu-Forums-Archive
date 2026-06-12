---
title: "Karmic - Gnome panel refreshes constantly after removing volume control applet"
date: 2010-02-10
forum: Desktop Environments
---

### Post by mister.zee.man on 2010-02-10
Hello all,

Long time lurker, first time poster...

I've been having issues with gnome-panel under karmic.

When I upgraded from Jaunty, a second volume control icon appeared in the panel. After I right clicked to remove it, the panel went into a continuous loop of refreshing then exiting. The focus changed to the panel on each refresh, making it almost impossible to select or click on anything. This happened even after a reset.

I did a clean install, but now the same issue has occured again. I've managed to ctrl-alt-f1 and kill the panel, but when I return to the desktop and relaunch from the terminal I get the following error:

** (gnome-panel:16719): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:16719): DEBUG: Adding applet 0.
** (gnome-panel:16719): DEBUG: Adding applet 1.
** (gnome-panel:16719): DEBUG: Adding applet 2.
** (gnome-panel:16719): DEBUG: Adding applet 3.
** (gnome-panel:16719): DEBUG: Adding applet 4.
** (gnome-panel:16719): DEBUG: Adding applet 5.
** (gnome-panel:16719): DEBUG: Adding applet 6.
** (gnome-panel:16719): DEBUG: Adding applet 7.
** (gnome-panel:16719): DEBUG: Adding applet 8.
** (gnome-panel:16719): DEBUG: Adding applet 9.
** (gnome-panel:16719): DEBUG: Adding applet 10.
** (gnome-panel:16719): DEBUG: Adding applet 11.

** (gnome-panel:16719): WARNING **: Invalid borders specified for theme pixmap:
        /home/zee/.themes/Divinorum-Blue/gtk-2.0/Buttons/button-normal.png,
borders don't fit within the image
** (gnome-panel:16719): DEBUG: Adding applet 12.
** (gnome-panel:16719): DEBUG: Adding applet 13.
** (gnome-panel:16719): DEBUG: Adding applet 14.
** (gnome-panel:16719): DEBUG: Adding applet 15.
** (gnome-panel:16719): DEBUG: Adding applet 16.
** (gnome-panel:16719): DEBUG: Adding applet 17.
** (gnome-panel:16719): DEBUG: Adding applet 18.
The program 'gnome-panel' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 2865 error_code 8 request_code 1 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I noted the error regarding my current theme, however, this wasn't installed last time around, so I think this can be ruled out. dpkg-reconfigure gnome-panel does not solve the issue.

Does anyone know of any fixes for this, before I start deleting my .gnome folders / reinstalling again?

Cheers!

---

### Post by vgrisham on 2010-02-10
It sounds like you got a bad installation iso download. Try downloading it again. Once you've done so, pop a terminal in the same folder as the iso and key md5sum followed by the exact name of the downloaded iso. That will verify the file's integrity *before* you install.

---

### Post by bobpaul on 2010-02-17
> **vgrisham said:**
> It sounds like you got a bad installation iso download. Try downloading it again. Once you've done so, pop a terminal in the same folder as the iso and key md5sum followed by the exact name of the downloaded iso. That will verify the file's integrity *before* you install.

I disagree with this answer; I don't think it sounds like this at all. 

To be clear, I'm having the exact same problem, but using the latest version of Linux Mint (which is based on Ubuntu Karmic). Before finding this, I had thought my problem was related to the mintMenu, but that doesn't exist in the parent's install. And my MD5 sum was fine.

mister.zee.man: 

Does this happen in new user accounts as well? It seems to be a problem for me after the second login. Deleting the .gnome* and .gconf* makes it go away, but the second tray applet re-appears eventually (ie, the second volume control).

---

