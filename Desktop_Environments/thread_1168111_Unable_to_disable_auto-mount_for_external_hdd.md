---
title: "Unable to disable auto-mount for external hdd"
date: 2009-05-23
forum: Desktop Environments
---

### Post by fabokzs on 2009-05-23
Hi,

I'm trying to stop my ubuntu 9.04 system auto-mounting my external hdd if it is attached to my computer.

I tried with different kind of hal configurations like:
```

<match key="volume.uuid" string="xxxxxxxx-xxxx">
    <merge key="volume.policy.should_mount" type="bool">false</merge>
</match>
```or
```

<match key="volume.uuid" string="xxxxxxxx-xxxx">
    <merge key="storage.automount_enabled_hint" type="bool">false</merge>
</match>
```The rule
```

<merge key="volume.ignore" type="bool">true</merge>
```Is working though, but in this case the hdd does not show up in places.

Does anybody have any idea to disable auto-mount for my device?

Zsolt

---

### Post by asmoore82 on 2009-05-24
This option was easily accessible in Ubuntu 8.04 LTS through "System -> Preferences -> Removable Media"

Now you have to Alt+F2 for "Run" and ...
```
gconf-editor
```

Then browse down to /desktop/gnome/volume_manager/
and uncheck the keys *automount_drives* and *automount_media*

I'm assuming/hoping that Gnome will consider this a regression and have a solution in the next release.
The "Media" Tab in nautilus preferences is a big improvement over the old "Removable Media"
but it seems that automounting preferences just slipped through the cracks.

---

### Post by fabokzs on 2009-05-24
Hi,
> **asmoore82 said:**
> This option was easily accessible in Ubuntu 8.04 LTS through "System -> Preferences -> Removable Media"

Now you have to Alt+F2 for "Run" and ...
```
gconf-editor
```Then browse down to /desktop/gnome/volume_manager/
and uncheck the keys *automount_drives* and *automount_media*

First the entry you mentioned was empty. After that I installed the gnome-volume-manager (I removed it, because I wanted to get rid of the totem), but the hdd is still auto mounted even if the two keys are set to false.

Zsolt

---

### Post by asmoore82 on 2009-05-25
Oops ... it moved on me AGAIN!

```
gconf-editor
```

and in "*/apps/nautilus/preferences/*"
the key is *media_automount*

:lolflag: growth is painful, but necessary.

---

### Post by fabokzs on 2009-05-29
It is working now, thank you very much

---

