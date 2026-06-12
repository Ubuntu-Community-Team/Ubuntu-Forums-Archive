---
title: "Dream Scenes"
date: 2010-05-16
forum: Desktop Environments
---

### Post by popppppz on 2010-05-16
Is there anything for Kubuntu simular to Windows Visa's Dream Scenes, other than the maps and globes wallpaper that comes with Kubuntu? Thanks.

---

### Post by Zorael on 2010-05-17
There is a video wallpaper plugin, yes, but it's not in the official repositories. There is a lucid (and a karmic) version of it in Sam Rog's ppa ([**ppa:samrog131/ppa**](https://launchpad.net/~samrog131/+archive/ppa)), though it's technically unsupported software.

```
$ sudo add-apt-repository ppa:samrog131/ppa
$ sudo aptitude update
$ sudo aptitude install plasma-wallpaper-video
```

The same ppa also includes a bunch of other wallpaper plugins. To grab them all;
```
$ sudo aptitude install ~nplasma-wallpaper
```

Note that this only installs the actual plugin - you would have to find a seemlessly looping video to use it with yourself.

---

### Post by popppppz on 2010-05-17
Thanks, I'll give ita try. :P

---

