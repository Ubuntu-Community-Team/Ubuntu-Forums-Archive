---
title: "Breezy boots into CLI. Again..."
date: 2005-10-31
forum: Desktop Environments
---

### Post by GrootBrak on 2005-10-31
After I had some display problems upgrading to Breezy, things were going fine. Last night I downloaded gnome-sudoku and re-loaded xsane. After a reboot, my PC boots back into the CLI again. I now have to log in at the CLI and then have to run the command "startx" I did a "sudo dpkg-reconfigure xserver-xorg" but it still won't load back. I checked my xorg.conf file and see that nothing has changed since the last back-up. I.e. my config file has never changed from the previous working state.

How can I rectify this annoying behavior?

---

### Post by suRoot on 2005-10-31
Have a look at /etc/inittab.

I'm an old RedHat guy, and with RedHat runlevel 5 is the GUI... but with Debian / Ubuntu it appears to be 2.

Look for this line:

```
id:2:initdefault:
```

Make sure it's set to 2.  If 2 is the wrong runlevel (and I'm pretty sure it's not based on the google search I just did), I'm sure someone will correct me.

---

### Post by GrootBrak on 2005-10-31
[QUOTE=suRoot]Have a look at /etc/inittab.

I'm an old RedHat guy, and with RedHat runlevel 5 is the GUI... but with Debian / Ubuntu it appears to be 2.

Look for this line:

```
id:2:initdefault:
```

Make sure it's set to 2.  If 2 is the wrong runlevel (and I'm pretty sure it's not based on the google search I just did), I'm sure someone will correct me.[/QUOTE]


Its is set at 2 as you suggested. I noticed this just below it.

> # Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

I do have multi-users. Interesting what you told me, but sorry its not what I need!!!:KS

---

