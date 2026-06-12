---
title: "gnome doesn't start after upgrade, where to start debugging?"
date: 2007-11-21
forum: Desktop Environments
---

### Post by tcoiler on 2007-11-21
Greetings, 

I recently updated some "stuff" on my 7.10 system.  I say stuff because the update manager showed there were updates available so I went ahead and updated them.  I don't remember what they were.  

So when I went to log in I entered my name and password in the gdm login screen.  Once logged in I ended up with nothing but a sand colored screen.  No indication that any of the gnome decorations such as tool bars, menus, etc were running.

I was able to ctl-alt-f1, start up an xterm, then gnome-wm so I could at least get some xterms and browser windows going and usable.  

Can anyone suggest where to look to start debugging this problem?

ps auxw  | grep gnome shows:

chip@teddy:~$ ps auxw | grep gnome
chip      6163  0.0  0.6   8788  3412 ?        S    07:09   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
chip      6256  0.0  1.5  52564  8128 ?        S    07:09   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=23
chip      6389  0.0  1.9  38472 10084 ?        Sl   07:10   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
chip      6507  0.0  1.9  38472 10084 ?        Sl   07:11   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
chip      6616  0.0  1.9  38468 10080 ?        Sl   07:11   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
chip      6668  0.0  1.9  38456 10064 ?        Sl   07:13   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
chip      6720  0.0  1.9  38460 10068 ?        Sl   07:14   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
root      6924  0.0  1.9  38448 10048 ?        Sl   07:18   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
chip      7123  0.0  0.3  13272  1724 tty1     SL   07:35   0:00 /usr/bin/gnome-keyring-daemon -d
chip      7126  0.0  1.3  19284  6812 ?        Ss   07:35   0:00 /usr/bin/gnome-session
chip      7187  0.0  0.1   4436   544 ?        Ss   07:35   0:00 /usr/bin/ssh-agent /usr/bin/ssh-agent /usr/bin/gnome-session
chip      7188  0.0  0.1   4432   544 ?        Ss   07:35   0:00 /usr/bin/ssh-agent /usr/bin/gnome-session
chip      7194  0.0  1.9  38468 10080 ?        Sl   07:35   0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
root      7548  0.0  1.4  22392  7712 ?        Ss   08:05   0:00 /usr/bin/gnome-power-manager
chip      7784  0.0  2.1  34216 11100 pts/7    S    09:11   0:00 gnome-panel
chip      7925  0.0  0.1   2976   748 pts/7    R+   18:04   0:00 grep gnome


Weird too because I don't see gnome-wm.  

Anyway, where to start?

Thanks in advance.

Chip

---

### Post by MrFSL on 2007-11-21
I think you might try dropping down to a terminal and running gnome-session. This way you might get good output on your problem.

---

### Post by tcoiler on 2007-11-21
Thanks for replying.  I tried running gnome-session and it doesn't provide any output, which is discouraging. 

I'll keep looking and see what I can find.  I'm always open to further ideas.

Chip

---

### Post by tcoiler on 2007-11-22
Well, the problem went away.  I don't really know what I did that fixed it but here is what I tried for any future unfortunates:

dpkg --configure -a
updated all packages
mv .gconfd to gconfd 
mv .gconf to gconf

rebooted.

There may have been other things too, but I don't remember making changes to any other configuration files or directories.

Sorry I don't have more information.

Chip

---

