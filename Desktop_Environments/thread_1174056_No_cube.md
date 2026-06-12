---
title: "No cube"
date: 2009-05-30
forum: Desktop Environments
---

### Post by _PEM on 2009-05-30
I have an used Dell latitude D510 than I recently installed Ubuntu 9.04 on. I love it except a couple of things;
Cube.
I have looked around on the web trying to find this but it looks like I'll have to bother you.
I can get the 4 desks and switch between them but  I have no cube effect.
Can you help me?

Thanks

---

### Post by nrostn on 2009-05-30
The cube is made in a project called Compiz. You can find all info about it on their site:
[http://www.compiz.org/](http://www.compiz.org/)

Installation and configuration information can be found following this URL:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by roman_platonov on 2009-05-30
install ccsm and in system-preferences-Compizconfig enable Cube

---

### Post by _PEM on 2009-06-02
In synaptic package manager it shows I have Compiz, I will download it from the site and install it if that would help. Will it?

Thanks

---

### Post by UbuntuNerd on 2009-06-02
you can also try this detail [guide](http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy)

---

### Post by _PEM on 2009-06-26
Thank you all for the the help. I am sorry I have taken so long to reply. Nothing has worked. Compiz seems to be installed and working, I plan to redownload and install it though. Right now I don't have time for the new toy but I will let you know soon as I try something more. I will have to go through all your posts aging to be sure I duoble tried everything.

THANKS EVERYONE

---

### Post by ad_267 on 2009-06-26
No, Compiz is installed by default, you don't have to install it again. That guide at help.ubuntu.com is for old Ubuntu versions and you'll likely just mess things up. The guide at my.opera.com looks more correct, but has unnecessary steps.

What you need is the configuration tool which lets you change the Compiz settings and enable the cube effect. To get this you need to install the compizconfig-settings-manager package from Synaptic or whatever method you prefer.

Then see the **How can I get the "cube" effect?** section at [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by _PEM on 2009-07-06
To install the package I ran some code. I am not sure if it went right, here were my results;

```

paul@paul-laptop:~$ sudo aptitude install compizconfig-settings-manager
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
paul@paul-laptop:~$ 
```
The instruction in the link you gave me are as fallows;

First, install compizconfig-settings-manager. Then, in **System > Preferences > Advanced Desktop Effects Settings**, go to General Options, Desktop Size tab, and make sure **Horizontal Virtual Size** is set to 4. Go back to the main window, and enable the Desktop Cube and Rotate Cube plugins.
You can "spin" the cube by pressing Ctrl+Alt+Left and Ctrl+Alt+Right, or hold Ctrl+Alt and click and drag.

I do not have Advanced Desktop Effects Settings in preferences.

---

### Post by _PEM on 2009-07-21
...So it looks like it didn't install.

---

### Post by ~sHyLoCk~ on 2009-07-21
> **_PEM said:**
> ...So it looks like it didn't install.
Your dpkg database lock wasn't available. Maybe you had synaptic open while attempting to install from terminal? 
Btw what graphic crd do you have? And do you have the driver installed for it? If yes then just install ccsm and play around with it.
[http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")

---

### Post by _PEM on 2009-07-23
Graphics card? I'm not the first owner of this laptop so the only info I have on it is what I found on the web. 
I would imaging the driver is installed as it displays everything fine ( minus the cube effect )

---

### Post by Dullstar on 2009-07-23
Odd.  I found this on Google.

Go to Synaptic Package Manager, then do a search for "Compiz Config"
Install compizconfig-settings-manager.
To run it, go to System > Preferences > CompizConfig Settings Manager

The desktop cube is under the desktop category.  Turn this on.

---

