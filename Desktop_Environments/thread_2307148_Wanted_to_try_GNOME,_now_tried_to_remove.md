---
title: "Wanted to try GNOME, now tried to remove"
date: 2015-12-22
forum: Desktop Environments
---

### Post by sbennettgso on 2015-12-22
So it's been a while since I messed with GNOME 3, and I wanted to mess around with it.  So I installed the meta package.

It was OK, but it seemed slower graphically than stock Ubuntu.  So I went to log into a Unity session, and all the sudden a bunch of my desktop settings in Unity are messed up.  The theme I was able to revert, but I can't get my wallpapers back - it's just giving me the stock background no matter what background (or set of backgrounds) I select.

Any clues?  I've done the standard stuff... restart, log out/in, purge GNOME, etc.

Thanks,
Scott

---

### Post by Frogs Hair on 2015-12-22
What Gnome package specifically ? A gnome shell installation is different from the gnome-desktop installation. You could start with the following and restart.

```
sudo apt-get autoremove 
``` ```
sudo apt-get install ubuntu-desktop 
```

---

### Post by flocculant on 2015-12-22
What's more likely useful is to find what apt-get install ubuntu-gnome-desktop adds to a stock ubuntu install - then remove all of that and then apt-get install ubuntu-desktop

You could do that in a virtual machine easily enough, in a xubuntu install it grabs 441 packages. I suspect similar happened - have you removed all of them?

---

### Post by sbennettgso on 2015-12-25
So apparently purging ubuntu-gnome-desktop does not remove certain things... the GNOME Tweak Tool was still controlling themes, backgrounds, etc.

I was able to set all that stuff through the tweak tool, and I'll probably just keep it.

Thanks,
Scott

---

### Post by kai15 on 2015-12-26
GNOME also can change your bootscreen, I had to use plymouth manager to change it back to the default one

---

