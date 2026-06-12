---
title: "Diplay"
date: 2010-02-15
forum: Desktop Environments
---

### Post by fahadmks666 on 2010-02-15
Hi

I am using an Nvidia Graphics Driver for the Display.
During the First Driver update of Ubuntu, I got the Nvidia Drivers installed on the computer of which I can change the resolution and Other features

But the issue is that, when I select an resolution and apply, it will be appliued, and when I restart the computer the next time, the resolution Goes back to the previous State making me to reconfigure the Display properties

What do I do?

I am really Fed up with this.

---

### Post by wojox on 2010-02-15
Open a terminal and run:

```
gksudo nvidia-settings
```

You need sudo priv's for it to stick. ;)

---

### Post by Grenage on 2010-02-15
**wojox** is spot on, you need to click *save to X configuration file* while you have root right.  Sometimes (and only sometimes) there are issues ani it won't write, simply crashing out.  You can usually get around that by clearing out the contents of /etc/X11/xorg.conf and trying again.

---

### Post by fahadmks666 on 2010-02-16
How do I delete the X Org file
 
I have tried to delete that file and It is giving me an error as no permission

---

### Post by Grenage on 2010-02-17
You'll need to use root rights:

To delete the file:
```
sudo rm /etc/X11/xorg.conf
```

To empty it:
```
sudo cat /dev/null > /etc/X11/xorg.conf
```

---

