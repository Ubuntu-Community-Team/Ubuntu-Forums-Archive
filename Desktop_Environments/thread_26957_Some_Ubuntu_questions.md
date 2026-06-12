---
title: "Some Ubuntu questions"
date: 2005-04-14
forum: Desktop Environments
---

### Post by jens on 2005-04-14
1. I use **/etc/init.d/gdm stop** to close the X server, can I do the same while using kdm: **/etc/init.d/kdm stop** ?

2. How comes I can't use something like **init 3** like in Fedora to close X ?

3. How do I change the default runlevel ?
I'd like to start in text mode.

PS: Very nice release though :) 

Thanks,
Jens.

---

### Post by heimo on 2005-04-14
[QUOTE=jens]
2. How comes I can't use something like **init 3** like in Fedora to close X ?
3. How do I change the default runlevel ?
I'd like to start in text mode.
[/QUOTE]

Default seems to have runlevel 2 and gdm started. This is not probably the most elegant way to disable it... but it should work.
 ```
sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/K13gdm
``` 

Then check the default initlevel is 2 (it should already be).  That's in /etc/inittab
 ```
# The default runlevel.
id:2:initdefault:
``` 

Now you can change to "GUI-mode" with /sbin/telinit 3 or just  ```
/etc/init.d/gdm start
``` 

Yes, I think the KDE's login manager is called kdm

---

### Post by jens on 2005-04-14
Thanks  :)

---

### Post by Alexander Kirillov on 2005-04-15
[QUOTE=jens]1. I use **/etc/init.d/gdm stop** to close the X server, can I do the same while using kdm: **/etc/init.d/kdm stop** ?

2. How comes I can't use something like **init 3** like in Fedora to close X ?

3. How do I change the default runlevel ?
I'd like to start in text mode.

PS: Very nice release though :) 

Thanks,
Jens.[/QUOTE]
 By default, Ubuntu has runlevels 2-5 identical. It uses runlevel 2 by default. This way, you can edit, e.g., runlevel 3 making it whatever you want, while keeping runlevel 2 in the default configuration.

---

