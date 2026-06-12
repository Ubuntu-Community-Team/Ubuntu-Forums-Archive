---
title: "Timed user session"
date: 2008-12-26
forum: Desktop Environments
---

### Post by americanknight on 2008-12-26
I've setup a computer with Edubuntu for my handicapped sister. I want her to be able to have a parent log her in, play games for an hour or two, and to then have her session expire, requiring a parental password for her to continue. Anyone know how to do this? :guitar:

---

### Post by headlessplatter on 2008-12-29
You could use a text editor to make a script like this:

#!/bin/bash
sleep 2h
shutdown -r now

This script will wait for two hours and then restart the computer. (The "shutdown" command requires root privileges, so if you launch it not as root, it will wait two hours and then fail to restart.)

Does Edubuntu use KDE or Gnome? If it's Gnome, here's a command that's supposed to just log out instead of restarting the whole machine:

gnome-session-save --kill --silent

(I haven't tried this command, so it might not do exactly what I think it does.) There's probably a command like this for KDE too, but I don't know what it is. Anyone?

Now, you just need to make your script auto-launch when you log in. In KDE, you can put a symlink to your script in:

~/.kde/Autostart

I don't know how to make something launch when you log in to Gnome. Anyone?

---

### Post by americanknight on 2008-12-30
Edubuntu's default is Gnome. I don't know where the script would go in the filesystem, but using the GUI I believe it can be activated by adding it to the list under System > Administration > Sessions.

So would I swap the last line of the original code you wrote with the logout command like this:

#!/bin/bash
sleep 2h
gnome-session-save --kill --silent

---

### Post by headlessplatter on 2008-12-30
yes.

---

