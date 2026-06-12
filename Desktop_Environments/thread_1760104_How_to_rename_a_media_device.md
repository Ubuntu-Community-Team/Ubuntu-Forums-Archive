---
title: "How to rename a media device ?"
date: 2011-05-16
forum: Desktop Environments
---

### Post by dargaud on 2011-05-16
Hello all,
when I plug in my phone, or my camera or plenty of other devices, the names show up in Dolphin as /media/BAAA-1DE8 or similar. How can I rename them to something more explicit ?

In Windows it's enough to right-click, [Properties] and change the name. If I do the same with kubuntu I get "permission denied" or if I'm root I get "could not rename file".

---

### Post by gsmanners on 2011-05-16
I'm not aware of the "proper" way, but the way I do it is:

```
sudo dosfslabel /dev/sdx8 NewLabel
```

Just make sure your label is less than 12 characters. For Linux formats, use:

```
sudo tune2fs -L NewLabel /dev/sdx8
```

---

### Post by dargaud on 2011-05-17
Thanks, that worked. Maybe this should be integrated in the [Properties] of the device...

---

