---
title: "When Gnome mounts something, how can I make it user force for my ipod?"
date: 2008-07-07
forum: Desktop Environments
---

### Post by underwater on 2008-07-07
Hello,

I can mount my ipod using the command line with 

```
sudo mount -t hfsplus -o rw,force /dev/sdc3 ipod/
```

However, it can't automount because the automount of Gnome doesn't use the force option that the HFS+ filesystem it has on it uses.  

I thought that I would just be able to right-click the icon after it was mounted, the correct ipod icon show sup once I manually mount, and add the "force" option by using the GUI.  This doesn't seem to work, though.

Am I suppose to still separate those options with commas?  Is there something I"m missing?  

Any advice?  Like I said, if I use the command line, I can make it mount fine, but it is just when I plug it in and Gnome tries to automount it fails because the HFS+ filesystem needs me to use the force command


Thanks in advance,
underwater.

---

### Post by reader4 on 2010-04-13
Me too.  Haven't found a solution yet.  Anyone?

---

