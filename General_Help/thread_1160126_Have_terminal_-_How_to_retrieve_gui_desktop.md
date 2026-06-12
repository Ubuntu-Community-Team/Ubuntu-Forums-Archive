---
title: "Have terminal - How to retrieve gui desktop?"
date: 2009-05-15
forum: General Help
---

### Post by opholdings on 2009-05-15
For those following the saga:  Grub wasn't working.  Reinstalled with live cd.  Now when I boot with the hard drive I only have a terminal.  No GUI desktop.

How can I reinstall the desktop?  Tried a lot of usplash commands to no avail.

Thanks

---

### Post by spcwingo on 2009-05-15
Sounds more like a xorg problem than packages.  Try this:

```
sudo dpkg reconfigure -phigh xserver-xorg
```

This will reconfigure xorg with the default settings.  After that run:

```
sudo /etc/init.d/gdm restart
```

If that doesn't work try:

```
sudo apt-get install --reinstall ubuntu-desktop
```

Hopefully that will at least get to the desktop.

---

### Post by opholdings on 2009-05-15
Thanks SPC.

Tried

```
sudo dpkg reconfigure -phigh xserver-xorg
```

Recieved: Need an action input.

Tried

```
sudo /etc/init.d/gdm restart
```

Stopping Gnome OK
Starting Gnome Fail

Tried

```
sudo apt-get install --reinstall ubuntu-desktop
```

Reinstalled 1.  But no GUI desktop to found on restart.  Still have terminal access.

---

### Post by spcwingo on 2009-05-15
Sorry, that first command should have been:

```
sudo dpkg-reconfigure -phigh xserver-xorg
``` (I forgot the hyphen)

Try that followed by the second command in my first post.

---

### Post by opholdings on 2009-05-15
Tried commands 2X's.

Still receiving the Gnome start = Fail.  

Other info I am seeing on start up:

kinit: no resume image and
tty1 after user name.

Tried all the kinit fixes and still cannot access the desktop.

Thanks for helping.

---

### Post by spcwingo on 2009-05-15
Hmmm, try this one last thing:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

if there are no errors, then:

```
sudo rm /etc/X11/xorg.conf
```

Just be very careful with the above rm command as it is the remove command.
Lastly:

```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
```

```
sudo /etc/init.d/gdm restart
```

If this doesn't work, then I am at a loss as what to try next...hopefully someone with more experience than me will chime in.

---

