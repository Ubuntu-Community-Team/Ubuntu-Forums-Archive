---
title: "Beryl Setting Manager won't open Python2.4"
date: 2007-01-18
forum: Desktop Environments
---

### Post by mexlinux on 2007-01-18
beryl-settings won't open, and I get the same error:
```

Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in ?
    import berylsettings
ImportError: No module named berylsettings

```

I have installed the packages proposed in [http://www.ubuntuforums.org/showthread.php?t=339335]("http://www.ubuntuforums.org/showthread.php?t=339335")
And it's still not working. I guess it's related to the python version or the python path, because:
I can see that the berylsettings module is placed in
```

/usr/lib/python-support/beryl-settings-bindings/python2.5

```

Althouhgt I have both python2.4 and 2.5 installed, 2.4 is the default version (If I just write python, that's the version I got).

How can I correct this problem?

If I run it with
```

python2.5 /usr/bin/beryl-settings

```

I get this error:

```

mcanedo@mcanedo-laptop:~$ python2.5 /usr/bin/beryl-settings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 1421, in <module>
    makeCategoryArea(Category)
  File "/usr/bin/beryl-settings", line 1268, in makeCategoryArea
    CatBasePixbuf = gdk.pixbuf_new_from_file_at_size("%s/%s"%(BaseDir,CatImages[Category.Name]),IconSize,IconSize)
gobject.GError: Unrecognized image file format


```

---

### Post by phorgan1 on 2008-04-24
> **mexlinux said:**
> beryl-settings won't open, and I get the same error:
```

Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in ?
    import berylsettings
ImportError: No module named berylsettings

```

I have installed the packages proposed in [http://www.ubuntuforums.org/showthread.php?t=339335]("http://www.ubuntuforums.org/showthread.php?t=339335")
And it's still not working. I guess it's related to the python version or the python path, because:
I can see that the berylsettings module is placed in
```

/usr/lib/python-support/beryl-settings-bindings/python2.5

```

Althouhgt I have both python2.4 and 2.5 installed, 2.4 is the default version (If I just write python, that's the version I got).

How can I correct this problem?

If I run it with
```

python2.5 /usr/bin/beryl-settings

```

I get this error:

```

mcanedo@mcanedo-laptop:~$ python2.5 /usr/bin/beryl-settings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 1421, in <module>
    makeCategoryArea(Category)
  File "/usr/bin/beryl-settings", line 1268, in makeCategoryArea
    CatBasePixbuf = gdk.pixbuf_new_from_file_at_size("%s/%s"%(BaseDir,CatImages[Category.Name]),IconSize,IconSize)
gobject.GError: Unrecognized image file format


```
similar problem fixed by using gdk-pixbuf-query-loaders to fix my
gdk-pixbuf.loaders file.
1) find your gdk-pixbuf.loaders file mine was:
   /usr/local/etc/gtk-2.0/gdk-pixbuf.loaders
2) check where gdk-pixbuf-query-loaders executable is.  I found two places.
   /usr/local/bin and /usr/bin.
    The one in /usr/local/bin generated output that didn't know about svg
    files, and caused the problem.
3) run the correct one and redirect its output to replace your
   gdk-pixbuf.loaders file.  In my case:

/usr/bin/gdk-pixbuf-query-loaders > /usr/local/etc/gtk-2.0/gdk-pixbuf.loaders

4)  Celebrate

---

