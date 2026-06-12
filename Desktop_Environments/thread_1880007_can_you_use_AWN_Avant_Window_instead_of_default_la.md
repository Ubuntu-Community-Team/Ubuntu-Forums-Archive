---
title: "can you use AWN Avant Window instead of default launcher in xubuntu 11.10?"
date: 2011-11-12
forum: Desktop Environments
---

### Post by skinfish on 2011-11-12
can you use AWN Avant Window instead of default launcher in xubuntu 11.10?

---

### Post by Dustintendo on 2011-11-12
You can, but it will pull down all of gnome as well

---

### Post by ankspo71 on 2011-11-13
Hi,
Yes you can, and it will install alot of additional software like Dustintendo said, but if all you need from AWN is a basic dock / application launcher with 3d effects, you could install AWN without the recommended applets or additional software. Then you can install the awn settings manager so you can configure AWN.

```
sudo apt-get install avant-window-navigator --no-install-recommends
sudo apt-get install awn-settings
```

Applets for AWN can be found by searching for the package names that start with awn-applet-***. You will need to keep an eye on how many packages they might want to install though.

---

### Post by brownbunny on 2012-10-25
well, as i did read this post AFTER i did 
sudo apt-get install avant-window-navigator awn-applets-all -y
in xubuntu 12.04
which resulted in numerous downloads, a restart and me not knowing what i did.
is there an easy way for a newbie to reverse what just happend?
the ubuntu software center shows lots of new installs, but that doesn't help me at this point.
anyones help is super-appreciated!

---

### Post by ankspo71 on 2012-10-28
Hi brownbunny.
I am unable to test the commands below because I have moved on to 12.10 where avant-window-navigator is no longer available, but these basic apt-get commands should work though.

```
sudo apt-get remove avant-window-navigator awn-applets-all
sudo apt-get autoremove
```

The first command will remove the main packages you installed. The second command should remove all of the additional packages (dependencies or recommended packages) that were installed and are no longer needed by other packages.

In my opinion, it is better to not use the -y option in apt-get commands so we can review what is going to be installed first.

---

### Post by brownbunny on 2012-10-28
everything is gone without a trace. lesson learned, superthanks!

---

