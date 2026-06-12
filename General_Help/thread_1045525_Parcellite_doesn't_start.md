---
title: "Parcellite doesn't start"
date: 2009-01-20
forum: General Help
---

### Post by aliennet on 2009-01-20
Hi,
   from a week or so I've some problems with Parcellite. I stop to function.
If i try to start it from terminal I receive this message:


> parcellite
GLib-ERROR **: /build/buildd/glib2.0-2.18.2/glib/gmem.c:136: failed to allocate 134559783 bytes
aborting...
Aborted

How can I solve it?

Thanks,
   Gianluca

---

### Post by steeleyuk on 2009-01-20
[http://www.getdeb.net/app/Parcellite](http://www.getdeb.net/app/Parcellite)

Latest version (0.9). Try that.

Ensure you delete the ~/.config/parcellite folder in your home directory. That will remove any config options you have previously set.

---

### Post by alperyilmaz on 2009-06-01
the files located in 
```

~/.local/share/parcellite
```

should be removed as well

---

