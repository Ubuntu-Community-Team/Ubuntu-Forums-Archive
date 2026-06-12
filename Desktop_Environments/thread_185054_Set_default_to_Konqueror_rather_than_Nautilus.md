---
title: "Set default to Konqueror rather than Nautilus"
date: 2006-05-31
forum: Desktop Environments
---

### Post by chriscando on 2006-05-31
Is there anyway to set my default file browser to Konqueror in Gnome? For instance when I put in my USB drive, it would be nice if Konqueror ran instead of Nautilus. Any ideas?

---

### Post by aysiu on 2006-05-31
This won't work fully, but it'll sort of work (I just tried it): ```
sudo dpkg-divert --divert /usr/bin/nautilus.old --rename /usr/bin/nautilus
sudo ln -s /usr/bin/konqueror /usr/bin/nautilus
``` The problem is that Nautilus isn't just a file manager--it manages the desktop, too, in Gnome. So, for example, if you have a drive on the desktop, and you right-click and select "Open," it'll open with Nautilus because Nautilus is what's displaying it on the desktop--it's already running in Nautilus.

However, if you go to Places > Home, your /home/username folder will open in Konqueror.

---

### Post by chriscando on 2006-05-31
Thanks, that works nicely. What exactly do those two commands do? Like you said when I goto Places > Home it opens in Konqueror, however nothing happens when I put in removable media. Also, just for reference, how would I undo those commands if desired.  Thanks for the reply.

---

### Post by aysiu on 2006-05-31
```
sudo rm /usr/bin/nautilus
sudo dpkg-divert --rename --remove /usr/bin/nautilus
```

---

### Post by Jussi Kukkonen on 2006-06-03
> What exactly do those two commands do?
First one diverts normal nautilus binary to nautilus.old (you could just move it, but that would be overwritten on next update). 

second command creates a symbolic link from */usr/bin/nautilus* to */usr/bin/konqueror*, so konq starts when someone tries to start nautilus.

More info: 
```
man dpkg-divert
man ln
```

---

### Post by CFBauer on 2007-05-04
Hey there.  New to Ubuntu, fairly new to Linux here.

I migrated to Ubuntu from a KDE distro, and I'm wanting to use dolphin rather than nautilus.  I tried the recommended code, and no luck.  

That's fine, I'll survive.

Problem is, I ran the 'fix' code aysiu recommended, and no dice. When I go'places > sda1' I get the error:

> Could not open location 'file:///media/sda1'
There was an error launching the default action command associated with this location.
Can someone help?  Thanks!

---

### Post by CFBauer on 2007-05-05
Welp, short story long I reinstalled Ubuntu.  I guess I'm just going to add a link to Dolphin on the panel then get in the habbit of clicking on it.

---

