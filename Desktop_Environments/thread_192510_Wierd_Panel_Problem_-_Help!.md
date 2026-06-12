---
title: "Wierd Panel Problem - Help!"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Marle on 2006-06-08
One of my panels got messed up (the text in the taskbar got distorted) and I decided the best way to fix it would be to delete it and create a new panel.  Well, when I created the new panel, the other panel went *blank*.  Now they won't respond to right-clicking, so I can't add to them, and I can't add any other panels.

Please help, I'm so confused.  I'm lucky I had a link on my desktop that opened up firefox, because I can't do anything else.  I can't open a terminal, I can't use any programs beside the few I have links to on my desktop.  Please help me. :(

---

### Post by bluevoodoo1 on 2006-06-08
Perhaps refreshing gnome-panel will make a difference.

Try pressing ALT+F2, type 'killall gnome-panel' and see if that brings it back to life. 

(You can run any program for which you know the command with ALT+F2)

---

### Post by Marle on 2006-06-08
ALT-F2 doesn't work either.  :(

Thank you very much for trying to help.  :)

---

### Post by musicinmybrain on 2006-06-08
Try "sudo dpkg-reconfigure gnome-panel". Just a shot in the dark.

---

### Post by Video Toaster on 2006-06-08
[QUOTE=musicinmybrain]Try "sudo dpkg-reconfigure gnome-panel". Just a shot in the dark.[/QUOTE]
That won't work if Marle can't get to a Terminal window...

You did try rebooting and/or restarting X (CTRL+ALT+BACKSPACE), right?

---

### Post by Marle on 2006-06-08
CTRL+ALT+F1 opens up a new ... session?  I don't know what to call it but it's a full-screen CLI that, unfortunetly, doesn't seem to affect my GNOME session, but I restarted from there when I first got my panel problems.   I just tried "sudo dpkg-reconfigure gnome-panel" in that, and when that didn't seem to do anything, I clicked CTRL+ALT+BACK and when I logged back into GNOME, I got the message "I've detected a panel already running and will now close".  Now I have no panels.  :-/

---

### Post by Video Toaster on 2006-06-08
[QUOTE=Marle]CTRL+ALT+F1 opens up a new ... session?  I don't know what to call it but it's a full-screen CLI that, unfortunetly, doesn't seem to affect my GNOME session, but I restarted from there when I first got my panel problems.   I just tried "sudo dpkg-reconfigure gnome-panel" in that, and when that didn't seem to do anything, I clicked CTRL+ALT+BACK and when I logged back into GNOME, I got the message "I've detected a panel already running and will now close".  Now I have no panels.  :-/[/QUOTE]
Try typing "sudo reboot" at TTY1 (CTRL+ALT+F1) to reboot the computer.  See if that helps.

**EDIT:**  I need to learn to read... I'm sorry.

---

### Post by Marle on 2006-06-08
I found a temporary workaround:

sudo apt-get install kubuntu-desktop

I miss gnome though.

---

### Post by Marle on 2006-06-09
[QUOTE=Video Toaster]Try typing "sudo reboot" at TTY1 (CTRL+ALT+F1) to reboot the computer.  See if that helps.

**EDIT:**  I need to learn to read... I'm sorry.[/QUOTE]

It's ok, don't feel bad.

I'm beginning to wonder if my lack of a ALT+F2 shortcut to get to the terminal isn't worse though.  It doesn't even work in KDE.  Is there a way to change keyboard shortcuts in KDE, and if so, will it then work in Gnome?  I'd really like to get my panels back, but I don't think I can without a terminal.

---

### Post by guzerat on 2006-06-09
Since Nautilus is at least partially working (the firefox-icon on the desktop), try right-clicking on the desktop -> open terminal

Edit: have you tried "killall [-9] gnome-panel" in the TTY?

---

### Post by bluevoodoo1 on 2006-06-09
[QUOTE=guzerat]Since Nautilus is at least partially working (the firefox-icon on the desktop), try right-clicking on the desktop -> open terminal[/QUOTE]

That will only work if the nautilus-open-terminal package is installed (it isn't by default). But I'd recommend getting it (if you can)... it' s useful for situations like this,

---

### Post by guzerat on 2006-06-09
[QUOTE=bluevoodoo1]That will only work if the nautilus-open-terminal package is installed (it isn't by default). But I'd recommend getting it (if you can)... it' s useful for situations like this,[/QUOTE]

Oh, I had no idea... it must have been the default behaviour in Breezy then? I did a dist-upgrade to Dapper so I guess it hangs around :)

Anyway, since the TTY:s are working it's no problem installing the package...

---

