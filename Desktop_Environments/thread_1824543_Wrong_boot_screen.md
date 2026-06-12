---
title: "Wrong boot screen?"
date: 2011-08-13
forum: Desktop Environments
---

### Post by mashmusic11235 on 2011-08-13
Hi. I recently installed several different desktop environments (KDE, LXDE, and XFCE) to test them out and see if any of them are better than GNOME. Anyway, onto the problem:

After I installed KDE, I rebooted my computer, and rather than the orange 'Ubuntu' booting screen, it was blue and said 'Kubuntu'. I thought this was normal, and ignored it. I eventually decided I didn't care for KDE, so I uninstalled it. I did several searches on the subject and I'm 100% sure I uninstalled all of it. However, my boot and shutdown screens still say 'Kubuntu' rather than 'Ubuntu'. This isn't a big deal, as it isn't affecting my computer at all, but I'd still like to know why this is happening, and how I can get my old boot screen back. 

Thanks in advance,
Alex

---

### Post by varunendra on 2011-08-14
Can't say for sure, but maybe it is some changed-configuration rather than package. Most of the configurations are reset to default if you choose 'completely remove' from synaptic for a related package that changed those configurations. But maybe not always.

For now, try reinstalling **ubuntu-desktop** metapackage from synaptic to set the screens to default. Again, not sure, but hope it should work.

---

### Post by mashmusic11235 on 2011-08-14
Thank you for responding.

I'll do that, but how do I go about setting my screens to default?

---

### Post by varunendra on 2011-08-14
> **mashmusic11235 said:**
> Thank you for responding.

I'll do that, but how do I go about setting my screens to default?
The reinstallation process should do it automatically, although I'm sure there must be some configuration file that may be edited manually to make desired changes, but I currently don't know about it.

---

### Post by wojox on 2011-08-14
```
sudo update-alternatives --config usplash-artwork.so
```

Select the splash screen of your choice.

---

