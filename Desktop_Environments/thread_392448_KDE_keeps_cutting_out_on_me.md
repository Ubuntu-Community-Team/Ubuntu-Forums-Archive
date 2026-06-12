---
title: "KDE keeps cutting out on me"
date: 2007-03-24
forum: Desktop Environments
---

### Post by Athanasius on 2007-03-24
I have been wanting to switch to KDE for a while, probably about a year but every time I install it (and I do mean every time) it does something to the x-server and I am stuck at a shell prompt.  I type startx and I get an error message.

This may all be vague but it is something that is really preventing me.  I installed Kubuntu-desktop and it completely messed up my Gnome install and everything. 

I have cruised the forums but I didn't really see any problems like this, does anybody know anything about this problem?

---

### Post by allix on 2007-03-24
Can you be more specific about the error-message?
kubuntu-desktop installs the KDE display manager, kdm, and might conflict with gdm(Gnome dis..). Not sure if this is whats causing your problems. Try ```
sudo dpkg-reconfigure gdm
``` and choose one of the two.

In my experience, installing both kubuntu-desktop and ubuntu-desktop creates a lot of problems. I recommend a clean Kubuntu installation. :)

---

### Post by Athanasius on 2007-03-24
I have also had this problem with a clean install as well.  I will be running it in a virtual machine for a while to see if I can reproduce the problem then I will get back to this.

---

