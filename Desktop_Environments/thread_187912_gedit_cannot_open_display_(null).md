---
title: "gedit: cannot open display: (null)"
date: 2006-06-03
forum: Desktop Environments
---

### Post by conradwoo on 2006-06-03
I'm sorta new to ubuntu and linux so sorry if this a stupid question.

When I first installed (yesterday), I was able to do stuff at the command line like "sudo gedit filename" but now whenever I type it in, all I get is

```
sudo gedit /etc/X11/xorg.conf
cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.

```

How do i fix this?

EDIT: Seems like I can open as a normal user but not when I try it as a "super-user"...

---

### Post by taurus on 2006-06-03
You can always use nano to edit your files,
```

sudo nano /etc/X11/xorg.conf

```

---

### Post by jiqiang on 2008-05-31
Thanks ,I also met the same question.

---

