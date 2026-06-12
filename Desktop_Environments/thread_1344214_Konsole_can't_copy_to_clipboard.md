---
title: "Konsole can't copy to clipboard"
date: 2009-12-02
forum: Desktop Environments
---

### Post by chaz572 on 2009-12-02
I've gotten into a state on my kubuntu 9.10 workstation where konsole can't copy to the clipboard.  Firefox can copy to / paste from the clipboard.  Pidgin can.  Everything else I've tested can.  If I copy from any other app, I can paste into konsole, but no matter how I try to copy out of konsole, it doesn't end up in the clipboard.  I usually just highlight, and expect that to work.  Until recently it has.  Now highlighting doesn't work, highlighting and then Ctrl+Shift+C doesn't work, and highlighting and then right-click select Copy from context menu doesn't work.

Here's how I'm guessing it happened....  We've got a pool of workstations here that all authenticate a common set of users over NIS, with all the user home directories on NFS.  Unfortunately, when we set up the current batch of workstations, we didn't standardize on distro, and several people installed whatever they wanted on their workstation without coordinating.  Mine is kubuntu 9.10.  But on Monday afternoon, I had to log into the X console of somebody else's workstation that was running OpenSUSE 11.1 to troubleshoot an issue on their workstation.  Stupidly, I logged in as me while I still was logged in as me on my workstation, and OpenSUSE proceeded to set up its desktop environment as a new user in my home directory while kubuntu was running on those same config files.  So who knows what it changed, but I'm thinking somehow it managed to break copy to clipboard in konsole.  At least everything else on my workstation seems fine so far.

I tried logging out of my kubuntu session, and logging back in.  Didn't seem to help at all.  I've been poking through config files under ~/.kde4, especially anything apparently related to konsole, but I don't see anything odd jumping out at me.  Does anybody have any ideas?

Thanks much!

---

### Post by ElSlunko on 2009-12-02
You sound a bit more experienced than I am but one experience I can offer is that Klipper (the clipboard manager that defaults in KDE) was dodgy. I installed gnome's parcellite and haven't had any issues since.

---

### Post by 23dornot23d on 2009-12-02
TRY SELECTING THE TEXT OR WHATEVER YOU WANT TO COPY

then just PRESS the MIDDLE mouse button in the application where you need the text to go to

( hopefully .... if you have one ..... its another method that usually works )

Yakuaka is another terminal ..... you could try adding that .... its in the Synaptic list ...

works well ...... see if it makes a difference ....

---

### Post by chaz572 on 2009-12-02
Welp, I'm happy (and chagrined) to report that the fix was simple.  I rebooted my workstation, and konsole magically regained its ability to copy to the clipboard.  I would have thought that a log out / log in would be sufficient to reset the desktop environment state, but that shows how much I know.

Much thanks to those who responded with ideas.  I probably should have tried rebooting before posting, but I grew up on a Unix "never shut it down" mentality.  :D

---

### Post by therico on 2010-01-21
I also have a similar issue; neither Konsole nor Kate copy anything into the clipboard. Perhaps it's one of those 'broken by apt update, reboot to fix' problems - will have a go.

Edit: confirmed - fixed after rebooting.

---

### Post by therico on 2010-04-23
The issue returned a few weeks later for no obvious reason. My "solution" was to switch back to GNOME.

---

