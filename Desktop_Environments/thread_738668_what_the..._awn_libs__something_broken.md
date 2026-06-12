---
title: "what the?... awn /libs / something broken"
date: 2008-03-28
forum: Desktop Environments
---

### Post by ixlam on 2008-03-28
I installed awn using >  
[http://ubuntuforums.org/showthread.php?t=572019&highlight=awn+repo](http://ubuntuforums.org/showthread.php?t=572019&highlight=awn+repo)
running gust (32bit) with all updates. I get error on launch>

avant-window-navigator
Gtk-Message: Failed to load module "gnomebreakpad": libgnomebreakpad.so: cannot open shared object file: No such file or directory
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_gconf_new


any takers?

---

### Post by warp99 on 2008-03-28
Do you have this library installed?

libgnomebreakpad.so

Run the following:

```
sudo find -name libgnomebreakpad.so
```

Run the command in the root directory. Post the results if you found the library and what directory you found it in. You may need to symlink the file. ;)

---

### Post by ixlam on 2008-03-28
nothing found!

---

### Post by warp99 on 2008-03-28
Well you're missing that library. I would retrace your steps to see if you missed anything.

---

### Post by ixlam on 2008-03-28
is that lib just a part of AWN or needed by other gnome apps like I think? how/can I install it seperately 

sudo apt-get install libgnomebreakpad.so
DONT werk!!

---

