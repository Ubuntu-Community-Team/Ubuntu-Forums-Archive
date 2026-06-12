---
title: "Upgrade, now can't log in as normal user"
date: 2006-03-22
forum: Desktop Environments
---

### Post by dannysauer on 2006-03-22
I have a laptop with Ubuntu 5.10.  It's been up for a month or two since the last reboot, but I've been apt-get update/upgrade-ing every few days anyway.  When I finally rebooted last night, after upgrading everything to current, GDM came up fine and I logged in, but Gnome never starts.  Or something doesn't start - all I get is the background change and a cursor.  The failsafe gnome login doesn't work, but the "just log me in with an xterm" does.  So I log in with an xterm, and I can run "sudo gnome-session" and that works, but running gnome-session as a regular user fails.

I completely wiped the home directory for the only user on the laptop (I don't store anything important on the laptop), and the .gnome and similar directories get recreated, but I still don't get a desktop.

I was getting suspicious messages about /dev/X not existing, but after starting up a session as root that directory exists (and it's mode 1777).  Now I see a message about being unable to link /dev/pty/something into /dev/X/.  So I'm wondering if something's up with the pam stuff that sets ownership of devices, or something along those lines.  Since things work for root, it's almost certainly a permission problem.  But I just haven't tracked it down.

All I've changed from stock on this install is that I created a script in /etc/network/if-up.d/ to start some firewall rules, but I've flushed uptables and disabled that script (this isn't a router anymore) to no avail.  I also added universe, multiverse, and backports.  Maybe I should run through and see what pakages are coming from the "unsupported" respoitories - I wonder if I got an unstable something-or-other.  I doubt it, though, since I have a pair of desktops (same i686 kernel, too) using the same repositories and same packages with no problem.

I'd appreciate thoughts as to where else to look... ](*,)

---

### Post by dannysauer on 2006-03-23
I'm not sure precisely what fixed it, but after messing around some more, I ended up installing the "ubuntu-desktop" pckage, and it now works.  Probably one of the gtk libs was unhappy?  I dunno, I could get metacity to run, but none of the gnome stuff would run.

Eh, it's "fixed" now.  Wish I knew what was wrong...

---

