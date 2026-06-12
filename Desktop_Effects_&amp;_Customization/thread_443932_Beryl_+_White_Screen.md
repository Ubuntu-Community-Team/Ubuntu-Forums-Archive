---
title: "Beryl + White Screen"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by homerj742 on 2007-05-14
Just did a fresh install of Feisty Fawn on my PC. Installed Beryl and now I got the white screen. 

Please help!

---

### Post by dfreer on 2007-05-14
install the correct video card for your system, and make sure direct rendering is enabled with this command:
```
glxinfo | grep rendering
```
without further information about your system (video card specs, contents of your /etc/X11/xorg.conf file) we really can't help much.
please note beryl is also beta software and does not work on all machines.

---

### Post by homerj742 on 2007-05-15
Well, I uninstalled all traces of beryl (i hope) by running synaptic package manager and doing a search for beryl. 

Next, I enabled the restricted drivers. 

I'm not used to it, because I had an old drive with Edgy on this same machine w/Beryl working. But now that I have a new drive I did a fresh install of feisty. 

With the restricted nvidia drivers enabled, and the glxinfo | grep rendering returning yes. How should I go about installing beryl

---

### Post by dfreer on 2007-05-15
ok, so direct rendering is working, w00t! now you can install beryl and IMO most importantly, 3D games!

```
sudo apt-get install beryl beryl-manager emerald-themes
```

That should get you going, add beryl-manager to the startup sessions (remove any other beryl reference that might be in there), and reboot and it should work. you may need to turn it on in beryl-manager the first time though. let us know if that worked for you!

---

### Post by homerj742 on 2007-05-15
Should I check for any other traces of beryl before trying to reinstall.

---

### Post by dfreer on 2007-05-15
well, you shouldn't unless you used one of the old methods. make sure that there is nothing in your startup sessions, if you edited /etc/gdm/gdm.conf you'll want to get rid of that, and if you created a seperate x login either delete it or just don't use it :) but those methods haven't been used for awhile so I think you'll be fine.

---

### Post by homerj742 on 2007-05-15
Did the install, put it in the start-up. Rebooted, and nothing. I see the beryl icon, but nothing is happening.

edit: DUH, i had to select it as the window manager. now it's working. hopefully it won't crash or nothin' :)

---

