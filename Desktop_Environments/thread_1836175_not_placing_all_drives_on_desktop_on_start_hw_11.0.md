---
title: "not placing all drives on desktop on start hw? 11.04"
date: 2011-08-30
forum: Desktop Environments
---

### Post by ottosykora on 2011-08-30
Whe I start xubuntu, all drives (volumes) on the computer seem to be mounted and icons are placed on the desktop.

Can this be avoided somehow? Where to find the setting?

---

### Post by BHEJU on 2011-08-30
Yes. But there is no built in setting for it. You have to install "ubuntu tweak". It's available in synaptic.
this utility has the parameter where you can show or hide mounted drives on desktop. And there are few other settings as well which you might find useful.

Cheers,

---

### Post by Toz on 2011-08-30
If you want to do some command-line magic, then:
```
$ cat /etc/udev/rules.d/10-local.rules
KERNEL=="sda1", ENV{UDISKS_PRESENTATION_HIDE}="1"

```
hides my /dev/sda1 (ntfs - winxp) drive from showing up anywhere. I can still mount it manually if I need it.

---

### Post by mcduck on 2011-08-31
the "standard way" would be to configure your drives in /etc/fstab, and set them to mount to any other location than inside /media. /mnt would be a good choice.

Only drives mounted in /media will appear on desktop.

BHEJU: Not only is that option in Ubuntu Tweak only related to Gnome desktop (not XFCE which this thread is about), the same option indeed *is* configurable with Gnome's own tools without installing anything. As are, really, pretty much all the things Ubuntu Tweak has (and many it doesn't have). Take a look at gconf-editor. ;)

---

### Post by ottosykora on 2011-08-31
> **mcduck said:**
> the "standard way" would be to configure your drives in /etc/fstab, and set them to mount to any other location than inside /media. /mnt would be a good choice.

Only drives mounted in /media will appear on desktop.



hmm , yes, but how is it done in ubuntu as oposed to xubuntu?

In ubuntu desktop , the drives can be mounted too and mount to the media as usual today, but they are not all on the desktop after boot.
What is set different between ubuntu and xubuntu?

---

