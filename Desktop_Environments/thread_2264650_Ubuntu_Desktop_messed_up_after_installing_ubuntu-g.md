---
title: "Ubuntu Desktop messed up after installing ubuntu-gnome-desktop"
date: 2015-02-09
forum: Desktop Environments
---

### Post by ichilton on 2015-02-09
Hi,

I've got an Ubuntu 14.10 installation and I wanted to be able to choose between the standard ubuntu desktop and gnome on login.

I did:
```
apt-get install ubuntu-gnome-desktop
```

Gnome seems to work fine, but when I log into Ubuntu Desktop, it's messed up, because it seems to be half Unity, half Gnome.

I get the Unity panel, but the top bar is Gnome - and terminal is messed up because it's using the system theme.

Is there a way I can have both, independent desktops on the same install?

Thanks,

Ian

---

### Post by tea for one on 2015-02-09
Good evening

I think that you should have installed Gnome Shell, because Ubuntu (Unity interface) is already built upon Gnome foundations.

```
sudo apt-get install gnome-shell
```

However, I'm not completely sure about the packages that arrive with the ubuntu-gnome-desktop command that you have used, therefore I am unable to advise if it safe to reverse your first command.

I suggest that you back up your important personal data.

Add synaptic via the Software centre (synaptic is a package manager, which is a bit more detailed than the Ubuntu Software Centre)

Use synaptic to see which packages will be affected by removing ubuntu-gnome-desktop.

Best wishes

---

### Post by ichilton on 2015-02-09
Ahh, great - thanks for that.

Ian

---

### Post by TheFu on 2015-02-10
Not ideal, but use different user accounts. That way the config files don't get mixed together.

---

