---
title: "Unity GUI broken."
date: 2014-08-22
forum: Desktop Environments
---

### Post by mongole on 2014-08-22
Hi,

I am running Ubuntu since about a year ago. But one of the last updates has broken my GUI rendering:

[ATTACH=CONFIG]255718[/ATTACH]

Any hint's how I can fix that?

Thanks,
Andi

---

### Post by mongole on 2014-08-24
I fixed it by uninstalling and installing unity with apt. I followed a post, which I can not find anymore.

first did following from a terminal (CTRL-ALT-F5):
```

sudo apt-get remove compizconfig-settings-manager
sudo apt-get remove compiz-fusion-plugins-extra
sudo apt-get remove compiz-plugins-extra
sudo apt-get purge compiz*

```

and then installed with following again:
```

sudo apt-get install unity-2d
sudo apt-get install ubuntu-desktop
sudo apt-get install ubuntu-desktop-2d
sudo apt-get install compizconfig-settings-manager
sudo apt-get install xserver-xgl
sudo apt-get install emerald
sudo apt-get install compiz-fusion-plugins-extra
sudo apt-get install git compiz-plugins-extra
sudo apt-get install compiz-plugins-extra
sudo apt-get install unity


sudo apt-get check
sudo apt-get install -f

```

surprisingly it looks fine now again! :)
maybe this helps somebody...

---

### Post by scarletford on 2014-08-25
I am trying this out because my desktop has gone crazy after an upgrade, but it couldn't find 'xserver-xgl', 'emerald', or 'compiz-fusion-plugins-extra' when trying to install. Any ideas?

---

