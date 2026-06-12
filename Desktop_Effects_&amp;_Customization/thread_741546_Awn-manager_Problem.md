---
title: "Awn-manager Problem"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by Redscare on 2008-03-31
Avant window navigator itself runs fine, but awn-manager doesn't; here's the terminal output:
```
redscare@redscare: awn-manager
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 44, in <module>
    from awnTheme import AwnThemeManager
  File "/usr/share/avant-window-navigator/awn-manager/awnTheme.py", line 26, in <module>
    import awnDefs as defs
  File "/usr/share/avant-window-navigator/awn-manager/awnDefs.py", line 23, in <module>
    from awn import CONFIG_DEFAULT_GROUP as DEFAULT_GROUP
ImportError: cannot import name CONFIG_DEFAULT_GROUP

```
Please help solve this?

---

### Post by Redscare on 2008-03-31
Incidentally, I also found out that i did not have an awn.so file under /usr/lib/python2.5/site-packages/awn/.

---

### Post by Redscare on 2008-04-01
anyone?

---

### Post by rustutzman on 2008-04-01
If you have Compiz functioning as it should maybe you should try the bazaar version of AWN. When I first set mine up I ended up removing the non-bzr version and replacing it with the bzr version. If this is the version you're running then I'm afraid I'm no help. 

Here's the URL for the bazaar AWN:
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

Russ

---

### Post by Redscare on 2008-04-01
yeah, im running the bzr. the problem does not lie with awn itself, i just can't set preferences or do anything because awn-manager does not run.

---

### Post by Redscare on 2008-04-01
I purged and installed awn that's not working. is it worth it to purge and reinstall python?

---

### Post by Redscare on 2008-04-01
UPDATE: I ran 
```
 export PYTHONPATH=/usr/lib/python2.5/site-packages
```
and got rid of teh config default error, but now i get this when running awn-manager:
```
Traceback (most recent call last):
  File "/Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 51, in <module>
    awn.vfs_init()
AttributeError: 'module' object has no attribute 'vfs_init'
usr/bin/awn-manager", line 51, in <module>
    awn.vfs_init()
AttributeError: 'module' object has no attribute 'vfs_init'
```

---

