---
title: "Uninstalling Evolution messed up my startup!"
date: 2009-02-03
forum: Desktop Environments
---

### Post by carignan.boy on 2009-02-03
I've been using Ubuntu for close to a year now.

I noticed that I *never* use the Evolution mail client. So I tried to uninstall it via Synaptic. When checking the verbose logs, I see that it's taking packages like gnome-panel and gnome-desktop and the such with it. I panic and quickly hammer Ctrl+c. 

Now, whenever I boot up, I get the Gnome Login just fine. After logging in, I get a black screen. I have to start nautilus, gnome-panel, gnome-power-manager, nm-applet (to name a few) manually via terminal. Also, running fusion-icon crashes GDM and logs me out, so compiz is also out of the question.

How can I fix this?

Here is what I tried : 
-Reinstalling Evolution
-Re-uninstalling Evolution, letting all "meta-packages" go with it, no dirty Ctrl+c
-Adding the programs I needed to the Sessions programs

Has this ever happened to anyone?
I know formatting and re-installing Ubuntu is an option. I'm not too fond of it though.

Thanks!

---

### Post by Hoaxe on 2009-02-04
try showing us your boot log to identify what the problem is specifically.

here are some instructions:
[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

---

### Post by ncubede on 2009-02-04
How about ```
 apt-get install ubuntu-desktop
```

---

### Post by carignan.boy on 2009-02-04
And how would I do that without downgrading to OOo 2.4?

---

### Post by Hoaxe on 2009-02-04
> **carignan.boy said:**
> And how would I do that without downgrading to OOo 2.4?

I think you're going to have to worry about that later...

---

### Post by ncubede on 2009-02-05
> **carignan.boy said:**
> And how would I do that without downgrading to OOo 2.4?

If you create a file e.g. called /etc/apt/sources.list.d/openoffice-ppa.list with the following content:
> 
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main


Then it should use OpenOffice 3, which is probably what you want...

---

### Post by carignan.boy on 2009-02-05
Ok. I turned on boot logging, nothing was effectively logged.

I changed the file with the sources and installed : ubuntu-desktop.

I still have the same problem. Oh and when I try to turn on "special effects" even on normal, I get logged out.

Any ideas?

---

### Post by ncubede on 2009-02-06
If you create a new user, can this one login to GNOME?

---

