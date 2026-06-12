---
title: "window boders in compiz missing"
date: 2006-08-23
forum: Desktop Environments
---

### Post by kthakore on 2006-08-23
I recently install xgl/compiz on gnome and ati 9200se, as a seperated session. But when I log in my windows borders go missing and there are no wobble windows or anything.

---

### Post by h00s on 2006-08-23
From: [http://www.ubuntuforums.org/showthread.php?t=131253](http://www.ubuntuforums.org/showthread.php?t=131253)

7. Start gconf-editor and go to "apps/compiz/general/all screens/options", and adjust "plugins" in the following order:

```
gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```

It MUST be in this order as there are dependencies between them. If you've already been playing with this from earlier debs - maybe from battlehorse, or maybe you rolled your own - this is an important step because it's very likely in the wrong order. Most people that are missing certain plugins or are missing things like "alt-switch" will find they need to correct this and restart.

---

### Post by kthakore on 2006-08-24
I have 'menu' missing and a few extra what sould I do:

```
reflection, blur. dbus, water, trailfocus, state, neg, bs, showdesktop, put
```

---

### Post by Cable on 2006-08-24
[https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz)

---

