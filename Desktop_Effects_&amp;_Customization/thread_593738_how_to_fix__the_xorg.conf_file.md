---
title: "how to fix  the xorg.conf file"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by blackmajik2021 on 2007-10-27
back when I was using feisty I tried to get dual monitors working and screwed around with xorg conf file and had my video settings all messed up ( weird resolution, desktop effects wouldn't work etc) now that ive upgraded i guess I have the same xorg settings and the new desktop effects wont work either. I get the error "the composite extension is not available". is there anyway for me to default my settings. yes i have restricted drivers enabled and im on an ati card.

---

### Post by skompier on 2007-10-27
> **blackmajik2021 said:**
> back when I was using feisty I tried to get dual monitors working and screwed around with xorg conf file and had my video settings all messed up ( weird resolution, desktop effects wouldn't work etc) now that ive upgraded i guess I have the same xorg settings and the new desktop effects wont work either. I get the error "the composite extension is not available". is there anyway for me to default my settings. yes i have restricted drivers enabled and im on an ati card.

When I was running Gutsy with my ATI card, this worked for me:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace

---

### Post by blackmajik2021 on 2007-10-27
so i used

sudo dpkg-reconfigure xserver-xorg

and now when i try to open desktop effects i get "details: failed to execute child process "desktop effects" No such file or directory" 

what the heck is up? :[

---

### Post by blackmajik2021 on 2007-10-27
I switched composite to 1 but now my desktop effects setting doesn't exist apparantly so its no use.

---

