---
title: "Upgraded from Warty, Xorg problems."
date: 2005-04-24
forum: Desktop Environments
---

### Post by Ricapar on 2005-04-24
I followed what the guide said, and upgraded. When I restarted the computer, I had an error saying something along the lines that the xserver was scewed up. I did this:

sudo apt-get remove xserver-xorg

then, this:

sudo apt-get install xserver-xorg

The error message is gone now, but now my screen is just black. I liked it with the error better :(

**update:** The error message is still showing, here is the Xorg log file:
[http://rafb.net/paste/results/ElbAEi12.html](http://rafb.net/paste/results/ElbAEi12.html)



Could anyone help me on fixing this?
I'll go crazy if I'm stuck using this crappy windows box that I'm on for much longer.


I have a new idea.  How would I go about removing everything that's related to XServer, and reinstalling that again, exact like it was when I first installed Ubuntu?

---

### Post by nad on 2005-04-24
Your log ends at this line:

(II) Initializing extension GLX

Try commenting out the: Load "glx"  line in your /etc/X11/xorg.conf file and post back your results.

---

### Post by Ricapar on 2005-04-24
[QUOTE=nad]Your log ends at this line:

(II) Initializing extension GLX

Try commenting out the: Load "glx"  line in your /etc/X11/xorg.conf file and post back your results.[/QUOTE]
 Got a bit further this time with that last edit. I commended out that line, and now it start up, and I can get to the login screen.

I log in, and then I get a small little dialog box in the center of my screen that has a light bulb on the side, and says "Xsession:" with an "OK" button below that. I clicked OK, and then got another one that was the same, but just said "|" where the last one said Xsession.

Then it comes up with a small command line box on the top left corner of the screen.

---

### Post by nad on 2005-04-25
Is the terminal window active? If so, read: ~/.xsession-errors

Anything interesting?

---

### Post by Ricapar on 2005-04-25
I got this inside that file:[indent]   /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "richard"
/etc/gdm/Xsession: Beginning session setup...
Xsession: run_parts() called, but "/etc/X11/Xsession.d" does not exist or is 
not a directory. Please report the installed version of the "xfree86-common" 
package and the complete text of this error message to 
<[email="debian-x@lists.debian.org"]debian-x@lists.debian.org[/email]>.
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator
[/indent]I'll check back here in the morning, 1AM here:smile:

---

### Post by nad on 2005-04-25
Your system is up but X and gnome are in an unusable state. The missing Xsession.d directory should contain scripts that start several services. I am at a warty install at the moment. My /etc/X11/Xsession.d directory is as follows:

20xfree86-common_process-args       75dbus-1-utils_dbus-launch
30xfree86-common_xresources         90xfree86-common_ssh-agent
50xfree86-common_determine-startup  99xfree86-common_start
55gnome-session_gnomerc

I did a search for default copies of these scripts but found none on this system. So it is not possible to recreate this directory by hand easily. The scripts are probably part of the gnome-desktop package.

One further suggestion is then to apt-get remove gnome-desktop and reinstall it.

Edit: I reread the error message and note that it refers to the xfree86-common package. Perhaps you should do a dpkg-reconfigure of this package first.

---

### Post by Ricapar on 2005-04-25
I also noticed that my /etc/X11/ directory is empty except for the xorg.conf file.. that's.. not good.


Gnome also starts up when I choose "Failsafe" mode for it.

---

### Post by nad on 2005-04-25
Any luck reconfiguring or removing and reinstalling the xfree86-common package?

---

