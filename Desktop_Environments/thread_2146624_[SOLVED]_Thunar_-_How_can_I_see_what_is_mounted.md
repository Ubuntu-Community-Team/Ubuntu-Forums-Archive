---
title: "[SOLVED] Thunar - How can I see what is mounted?"
date: 2013-05-19
forum: Desktop Environments
---

### Post by 2CV67 on 2013-05-19
Just struggling a little with Xfce after years of Gnome & Lxde...

In Nautilus, mounted partitions & drives are indicated by a "triangle over bar" icon.
Non-mounted partitions are shown in the left pane but without the icon - right?
When I hot-plug my camera, it appears with the icon & I know it's mounted.

In Thunar, all partitions, mounted or not, have a similar icon?
To mount a partition, I have to click on it, but the icon doesn't change?
To unmount a partition, I have to click on the icon, but the icon doesn't change?
I can't see at a glance which partitions are mounted & which are not?
When I hot-plug my camera, it appears with the icon but I don't know if it's mounted or not.
In fact it is not mounted & I have to click on it to mount it, but the icon doesn't change...

Or am I missing something?

I have searched a LOT & don't find any simple documentation on basic Thunar.

---

### Post by sudodus on 2013-05-19
I just checked and I see the same. Nautilus and PCmanFM work as they should, but Thunar shows those eject symbols all the time. I don't know if it is intended to be like that or if it is a bug.

Anyway, you can always resort to the old ***df*** command, which shows what is mounted and where it is mounted.

```
df
```
or if you prefer 'human readable numbers'
```
df -h
```

---

### Post by Dennis N on 2013-05-19
There is a difference in the icon used for the device (to it's left). A mounted one is a bit darker. It also depends on the icon theme in use. Some show a more noticeable difference. 

Solution: If you install the Places plugin in the panel, it shows unmounted devices as greyed out. Very clear to see what is mounted. 

In Xubuntu 12.04 and 12.10, there were always eject symbols as you observed, but In Xubuntu 13.04 there are no eject symbols at all for any partitions mounted or not - the eject symbol only shows for external devices (usb).

---

### Post by 2CV67 on 2013-05-19
> **Dennis N said:**
> There is a difference in the icon used for the device (to it's left). A mounted one is a bit darker. It also depends on the icon theme in use. Some show a more noticeable difference. 

Ah - Yes!
You need sharp eyes with my icons, but the difference IS there when you know where to look!

Many thanks!

---

### Post by Dennis N on 2013-05-19
Also, if you have the device icons showing on the desktop, the tootip on mouseover will tell you if the device is mounted or not in addition to the difference in the icon.

---

### Post by 2CV67 on 2013-05-22
Thanks for your helpful comments, Dennis N.

I happen to prefer my desktop without Device Icons, so I miss out on that one.

I tried the "Places" plugin & that certainly shows things clearly.

Actually, now you pointed it out, I can live with the faint difference in icons (on the left) where I was expecting to see big differences in icons on the right.

Thanks again!

---

