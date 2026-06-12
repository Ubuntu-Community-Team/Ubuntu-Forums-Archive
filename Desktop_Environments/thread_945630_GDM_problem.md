---
title: "GDM problem"
date: 2008-10-12
forum: Desktop Environments
---

### Post by HanaD on 2008-10-12
Have been running Ubuntu 8.04  everything was working fine but suddenly i got disconnected from internet and following message appeared:

Could not start the X 
Server due to some internal error.
Please contact your sysem adminstrator
or check your syslog to diagnose.
In the meantime this display will be 
disabled. Please restart GDM when the 
problem is corrected"

I could not boot in through the normal mode so i booted through the recovery mode and tried to do stuff explained in some other similar forums...
following is what i did:

/usr/bin/startx

Output
mktemp: cannot create temp file /tmp/serverauth.BXqGJx4736: Read-only file system
/usr/bin/startx: line 139: cannot  create temp file for here document: Read-only file system
/usr/bin/startx: line 149: xauth: command not found
/usr/bin/startx: line 151: cannot  create temp file for here document: Read-only file system
/usr/bin/startx: line 149: xauth: command not found
/usr/bin/startx: line 151: cannot  create temp file for here document: Read-only file system
/usr/bin/startx: line 162: xinit: command not found
/usr/bin/startx: line 166: xauth: command not found
root@hana:~#

---

### Post by forger on 2008-10-12
Try shut down, leave it for 30 seconds and boot again

I hope that you can start the normal mode now.. if not, what errors do you get?
Can you press ctrl+alt+F1 or does it drop you itself to a console login screen?

In normal mode, try this:
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```

If it still doesn't load up gdm, do:
[COLOR="Red"]**WARNING! You'll have to re-enable your display/graphics driver**[/COLOR]
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start

```

what were you specifically doing when this happened?

---

### Post by HanaD on 2008-10-12
If i go to normal startup it says segmentation fault

but this time when i went to recovery mode it gave me 3 options 

Xfix
and there were 2 others which i do not remember.

I did this xfix and it has enabled me to start the GDM somehow, 
I do not know what happened but atleast i can logon to my desktop.
I am worried if i should log off my pc again...

---

### Post by forger on 2008-10-12
Well, let's hope it doesn't happen again :)

---

