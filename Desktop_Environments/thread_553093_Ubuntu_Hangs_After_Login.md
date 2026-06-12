---
title: "Ubuntu Hangs After Login"
date: 2007-09-17
forum: Desktop Environments
---

### Post by mattgb on 2007-09-17
Hi Folks.
I've had Fiesty Fawn installed on my Core2 Duo PC for about two months now - and as an old Debian fan, I'm now loving Ubuntu!

Everything has been working well until recently when I pulled the cover off my PC for a bit of hardware swapping. I removed a PCI wireless card, added an Ethernet NIC, and swapped out an IDE drive in there (system boots from a SATA drive). 

Upon next bootup FSCK launched saying something like "file system check has not been run in over x days, running now...". However, right at the end of a disk scan it reported some kind of error then suddenly rebooted the PC. 

Anyway, ever since the hardware swap, fsck, and possibly other "tweaks" I have not been able to login to the Nautilus desktop. After I type the correct username/password, the login box disappears and it just hangs with a maroon screen and a movable mouse showing a standard white arrow icon. 

I can use ctrl+alt+backspace to reset gdm, but same issue when I try to login again.

I can use the "Failsafe Xterm" login and then can run "nautilus" at the $ prompt which produces a file browser and a few desktop icons but no "Start bar" or program launcher.

Also, I've used "tail -f $HOME/.xsession-errors" during a login attempt and I get: 

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mberry"
/etc/gdm/Xsession: Beginning session setup...
[B][COLOR="Red"][: 12: closing paren expected
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"[/COLOR][/B]

So any idea what's broken?

Thanks,
Matt.

---

### Post by inik on 2007-09-17
maybe problem is - user rights  on some folders in ~ directory
try sudo chown -R <user>:<usergroup> ~/
i'd similar issue once on my suse box after moving home directory to new drive (because i used root account)

---

### Post by mattgb on 2007-09-18
Sounds plausible, but alas - I set myself as owner of all files in $HOME but it hasn't helped.

Any idea which log file to look in for an error when gdm just won't launch nautilis after login?

---

### Post by mattgb on 2007-09-18
Looks like I've fixed the issue. I searched for "Xsession 12: closing paren expected" as per the line in ~/.xsession-errors I mentioned above. 

I then found this post in the Ubuntu forums (so looks like a specific ubuntu issue, not just gnome, Xsession or debian): "[ x server session doesn't start correctly]("http://ubuntuforums.org/showthread.php?t=324849")" 

The post suggests:

sudo aptitude update
sudo aptitude install ubuntu-desktop

Which has now restored my desktop to all it's former glory! Woohoo!
:guitar:

---

