---
title: "n00b@panic - x doesn't start..."
date: 2005-09-29
forum: Desktop Environments
---

### Post by roots on 2005-09-29
hi there...

i dont know what went wrong when synaptic removed the alsa base package, but after a reboot some time later it left me with a command line login prompt.
duh, there i am, not knowing what to do. obviously x doesn't start and so does gnome, but what to do now?

cheers,
.roots

---

### Post by Dayylin on 2005-09-29
Hiya Root,

Do you mean it just boots up to the login prompt? Did you try startx or did that not work?

Brian

---

### Post by zAo on 2005-09-29
If you only removed the alsa base package, login on the console. Then run:
```
sudo apt-get install alsa-base
```
After that, try this (or reboot):
```
/etc/init.d/gdm restart
```

---

### Post by roots on 2005-09-29
thanks for the quick replies!

@ zAo: i already did that. re-install was successful but the reboot brought me to the text mode login prompt again. btw. there is now "gdm" whatsoever to restart?!

@ Dayylin: yes, the text mode login prompt. startx worked and brought up some other non-gnome window manager (i always forget the name...).

any more ideas?
what could have been wrecked that usually makes x btw. gnome start up after boot? 


cheers,
.roots

---

### Post by Dayylin on 2005-09-29
To be honest, I am not sure why it did it, but this thread may help on how to get it to boot back to X  [http://www.ubuntuforums.org/showthread.php?t=7019]("http://www.ubuntuforums.org/showthread.php?t=7019")

---

### Post by heimo on 2005-09-29
roots: I would probably try to
```
sudo apt-get install ubuntu-desktop
```
just to make sure that you have all the relevant stuff installed. Does this give any error messages?

---

### Post by roots on 2005-09-29
@ dayylin: are you sure this is the right thread??? ;-)

however, after another reboot, which again brought me to the login prompt, i did "startx" again and this time it brought up gnome! subtle is the lord...

.roots

---

### Post by roots on 2005-09-29
thanks heimo!

you know what happened? sorry, but i couldn't believe what i saw:

```

....sudo apt-get install ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gaim gdm gimp gimp-data gnome-btdownload gnomemeeting gthumb sound-juicer tsclient xchat xchat-common xsane
Suggested packages:
  libzephyr3 msttcorefonts gimp-help-en gimp-help libgimp-perl gimp-data-extras xnest libnet-google-perl
  hylafax-client mgetty-fax gv gocr
Recommended packages:
  gimp-svg libpt-plugins-v4l libpt-plugins-avc libpt-plugins-dc mozilla-browser www-browser
The following NEW packages will be installed:
  gaim gdm gimp gimp-data gnome-btdownload gnomemeeting gthumb sound-juicer tsclient ubuntu-desktop xchat
  xchat-common xsane
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11,4MB of archives.
After unpacking 63,0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

```

i confirmed and he installed all the "previously deselected" packages!?

HOW COULD THAT HAPPEN?

.roots

---

### Post by Dayylin on 2005-09-29
Bah posted the wrong link lol. That's what happens when you don't get enough coffee in your system. Glad it's working now though :-)

---

### Post by roots on 2005-09-29
yup, thanks to all who helped!

now, after reinstalling the desktop stuff and rebooting, everything is fine as it was before. i really don't know what happened...


cheers,
.roots

---

