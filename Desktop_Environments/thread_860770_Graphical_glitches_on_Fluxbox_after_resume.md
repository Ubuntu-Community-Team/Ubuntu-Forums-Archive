---
title: "Graphical glitches on Fluxbox after resume"
date: 2008-07-15
forum: Desktop Environments
---

### Post by Hooya on 2008-07-15
I can hibernate and resume with good success on my laptop running 8.04 32-bit with Fluxbox as a window manager.  The issue is that when I resume from Hibernate the window manager has a bunch of weird graphical glitches.

The borders around windows are missing/transparent although title bars are fine.
The arrows normally present on the taskbar to switch workspaces or windows are gone, although the buttons are still functional.

GKrellm has weird parts of it missing.
Anything in the center of the screen gets sorta stuck, like the middle square region of the screen won't refresh properly.
Ctrl+alt+backspace to restart X does not solve the problem.  In fact, a reboot does not solve the problem!  I have to actually Shut Down and Reboot cold to get rid of the errors.

Any idea what could cause this?  I can post a screenshot if necessary, but it's hard to work with the environment if I can't always see what I'm doing.

---

### Post by p_quarles on 2008-07-15
I can virtually guarantee you that this is a problem with X rather than with Fluxbox (which is extremely simple as graphical software goes -- it's not responsible for enough to allow it to cause these kinds of problems).

Thus, if you could describe your system, that could help.

---

### Post by Hooya on 2008-07-16
It's a Toshiba A15 S129 Laptop.
Upgraded to 768MB RAM and a miniPCI WiFi card, but otherwise the same as retail...  old as it is.
Intel 852GM graphics chipset with 32 MB shared RAM (system memory is 740MB).

Otherwise it's a pretty vanilla Xubuntu install, but I removed Xfce (using a package list I found, so I really did remove most of Xfce) and installed Fluxbox.  Of course I have other stuff on here as well, but I don't know what would be relevent.  /home is on it's own partition.

I have kernel 2.6.24-19.

Oh, and I use /etc/acpi/hibernate.sh to hibernate.

---

### Post by spupy on 2008-07-16
When you resume, try to switch to a virtual console with Ctrl+Alt+F1 and then back to the Xserver with Ctrl+Alt+F7. I had similar problems with resume. Switching to a virtual console and back fixes it for me. There is a setting somewhere in /etc that does that switching automatically and seamless.

---

### Post by Hooya on 2008-07-16
Switching to the F1 terminal and back to the F7 desktop doesn't fix the problem.  It does redraw the screen, so any temporary errors go away, but I can do the same thing by minimizing and maximizing my windows.  The persistent errors (like the missing taskbar buttons, minimize and maximize buttons, and the center screen redraw issue) are still there.

Like I said, so far even "sudo reboot now" doesn't fix the issue, I have to "sudo shutdown -h now" and start the machine with the power button.

Everything else works great: sound, wireless, just bad graphical glitches.

---

### Post by spupy on 2008-07-16
> **Hooya said:**
> Switching to the F1 terminal and back to the F7 desktop doesn't fix the problem.  It does redraw the screen, so any temporary errors go away, but I can do the same thing by minimizing and maximizing my windows.  The persistent errors (like the missing taskbar buttons, minimize and maximize buttons, and the center screen redraw issue) are still there.

Like I said, so far even "sudo reboot now" doesn't fix the issue, I have to "sudo shutdown -h now" and start the machine with the power button.

Everything else works great: sound, wireless, just bad graphical glitches.

Might be an issue with the video card (drivers). Is there only one driver available for your video card? If there is a way to, i don't know, "flush" the memory of the card, so it redraws everything correct?

On my pc, if I use ubuntu and then restart to Gentoo, I can see the ubuntu wallpaper in gentoo for about 1 second...

---

### Post by gopherdoc on 2008-10-28
I am having the exact same problem...just wondering if a solution was found

---

### Post by spupy on 2008-10-28
Just a quick test. Try the program **xrefresh**. (in terminal, might not be installed)

---

### Post by Hooya on 2008-10-28
I think I ended up fixing the problem by installing a different program to hibernate things and that fixed the graphical error.  My WLAN rate drops to 1, but that's easy to fix.

sudo aptitude install hibernate

Try that.

---

### Post by gopherdoc on 2008-10-28
I can confirm xrefresh does not fix the error.  Neither does killing x with ctl+alt+bksp and restarting x.  I run gentoo, so aptitude install hibernate won't work, but i'll try re-emergine hibernate-script to see if that does anything.  Thanks!

---

### Post by gopherdoc on 2008-10-28
reinstalling hibernate-scripts and setting all alpha values in ~/.fluxbox/init to 255 seemed to do the trick

---

