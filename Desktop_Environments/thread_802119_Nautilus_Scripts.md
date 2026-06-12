---
title: "Nautilus Scripts"
date: 2008-05-21
forum: Desktop Environments
---

### Post by Snocrash on 2008-05-21
What happened to the nautilus scripts menu?? I have all the scripts I want installed and the script manager. But no menu to use them. If I sudo nautilus, the scripts menu is there, but not for my normal user...This is no good since the converted file are now owned by root.

Can anyone help???

Thanks,

-Sno

---

### Post by Snocrash on 2008-05-21
Bump

---

### Post by wdaniels on 2008-05-21
This is probably just a permissions problem - the scripts menu is not shown if there are no scripts, so if the scripts are owned by root then that would seem to be the problem for the normal user.

Where do you have the scripts installed? Normally it's ~/.gnome2/nautilus-scripts I think. You should be able to "sudo nautilus" then go to that location and change ownership to your user in the properties (also add executable permissions) or use chown/chmod commands in a terminal to do the same.

---

### Post by VMC on 2008-05-21
I don't have any Nautilus scripts, but I do have the mentioned directory, but its empty.
What are Nautilus-scripts? Something you make yourself?

~/.gnome2/nautilus-scripts

---

### Post by wdaniels on 2008-05-21
There are no Nautilus scripts installed by default in Ubuntu. You can write your own, or use ones written by others. For more information about them see [here]("https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-440.html"). For a good collection of existing scripts see [here]("http://g-scripts.sourceforge.net/").

---

### Post by Snocrash on 2008-05-22
Thanks wdaniels,

After some poking around, I found the scripts I installed through Synaptic in /usr/share/nautilus-scripts. I just copied them into ~/.gnome2/nautilus-scripts and everything works fine now. Odd the install does not let a normal user use the scripts in /usr/share. 

Thanks again,

-Sno

---

