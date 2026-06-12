---
title: "X Mouse Pointer"
date: 2006-02-26
forum: Desktop Environments
---

### Post by sprucio on 2006-02-26
I'm trying to get back the regular X mouse pointer in Breezy Badger.

If I run "update-alternatives --config x-cursor-theme" I get a message saying that this is the only available pointer.

I have installed the package "xcursor-themes" but this doesn't seem to contain much either.
```
[root@spruce ~]# dpkg -S xcursor-theme
xcursor-themes: /usr/share/doc/xcursor-themes/copyright
xcursor-themes: /usr/share/doc/xcursor-themes
xcursor-themes: /usr/share/doc/xcursor-themes/changelog.Debian.gz
```

Can anyone point me in the right direction on how I can get the default mouse pointer in X?

---

### Post by naked on 2006-02-27
Have you looked in Menu> System> Preferences> Mouse> 'Pointers tab'?

You should be able to select different themes here.

L

---

### Post by sprucio on 2006-02-27
The pointer I'm looking for is not there. I'm looking for the default X cursor.

---

### Post by sprucio on 2006-02-28
Can anyone tell me which packages I need to install in order for me to get more themes for the mouse?

---

### Post by sprucio on 2006-03-01
Actually, I realized that I used the wrong option. It should have read: ```
$ dpkg -L xcursor-themes
```

Now, I final few lines of the output are ```
/etc/X11/cursors/core.theme
/etc/X11/cursors/handhelds.theme
/etc/X11/cursors/redglass.theme
/etc/X11/cursors/whiteglass.theme
```

If I run "update-alternatives --config x-cursor-theme" I get ```
[root@spruce app-defaults]# update-alternatives --config x-cursor-theme

There is only 1 program which provides x-cursor-theme
(/usr/share/themes/Human/cursor.theme). Nothing to configure.
``` So what do I need to do to configure this correctly?

---

