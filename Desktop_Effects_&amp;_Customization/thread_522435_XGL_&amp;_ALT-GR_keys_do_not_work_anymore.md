---
title: "XGL &amp; ALT-GR keys do not work anymore"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by GoldWing on 2007-08-10
My XGL and Beryl/compiz is working great, but my keyboard is experiencing problems now.
All my keys that I have to type with the AltGr combination are not working anymore.
I have to say I have a belgian keyboard layout (azerty).

When I switch to a normal session, the combinations are working again. My keyboard layout is the same in System/preferences.

---

### Post by Lapeth on 2007-08-29
Try this:

[http://bbs.archlinux.org/viewtopic.php?pid=199501]("http://bbs.archlinux.org/viewtopic.php?pid=199501")

In case that page moves or gets deleted, here's the essentials:

```
echo 'keycode 113 = Mode_switch' >> ~/.Xmodmap
xmodmap ~/.Xmodmap
```

Worked like a charm for me.

---

### Post by ricardoec on 2007-08-31
:lolflag:Thanks... !!

---

