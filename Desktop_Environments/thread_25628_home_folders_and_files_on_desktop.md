---
title: "/home/ folders and files on desktop"
date: 2005-04-10
forum: Desktop Environments
---

### Post by joplass on 2005-04-10
If I creat a folder or add a file in /home/<username> it also appears on the desktop.  If I delete it from the desktop it's also gone from /home/<username>.
How can stop this from happening?
Thank you,

---

### Post by TravisNewman on 2005-04-10
Have you told Gnome to use your home folder as the desktop using the config editor? I've done that before myself and totally forgotten about it.

---

### Post by joplass on 2005-04-10
I know I have visited the editor to for example bring up icons on my desktop but I don't remember touching the portion about Gnome using the home folder as my desktop.  I might have done it though because this is a brandy new installation of Hoary on my notebook and since last night I am doing all I can to make it shine.  :-P 
Any idea how I can fix my little problem?
Thank you,
Meanwhile I will go back to the editor and try to find out where I made a poop.

---

### Post by pip on 2005-04-11
Use the GConf configuration editor to set the following key to false:

/apps/nautilus/preferences/desktop_is_home_dir

---

