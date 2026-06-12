---
title: "GUI broken after Upgrade"
date: 2005-10-13
forum: Desktop Environments
---

### Post by munroe on 2005-10-13
Fairly new user here, installed Hoary about 2 months ago and I've been happy with it since. I upgraded last night(edit sources.list, update, dist-upgrade) and it would no longer load the GUI login screen, terminal only. I can still log in, so I'm assuming it's a problem with my xorg.conf.

I looked around before posting this, but I couldn't find a similar problem. Anybody know what's going on?

---

### Post by Qrk on 2005-10-13
Type at the terminal propmt:
sudo dpkg-reconfigure xserver-xorg

It will ask you some questions; I'd recommend vesa insted of nv. You can also set your resolution, mouse, etc. If it doesn't work the first time, be sure to try some different options.

---

### Post by doublejoon on 2005-10-13
I did this too and the gui failed on me. I noticed in my /home directory that the .ICEauthority file belonged to root.

I just chowned it back to my ownership....and it worked!

chown name:name .ICEauthority  :)

---

