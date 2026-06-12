---
title: "gnome-terminal windows size on open"
date: 2008-11-23
forum: Desktop Environments
---

### Post by graysky on 2008-11-23
How can I set my launcher to gnome-terminal to open the shell window to a specific size?  Currently it's roughly 577x385... I'd like it to be a bit wider, say 620x385.

I tried it with the [color=blue]--geometry 620x385[/color] but that made it enormous, way beyond the dimensions of my monitor.

Thanks!

---

### Post by hictio on 2008-11-23
That's because:

> 
The WIDTH and HEIGHT parts of the geometry specifications are usually measured in either pixels or characters....


Take a look at the man page of X, pretty likely you won't have it on an Ubuntu box, because it uses Xorg, I have take a peek at my FreeBSD box :D
The geometry is applied like this:

```

--geometry WIDTHxHEIGHT+XOFF+YOFF

```

Do some tests with smaller values, like:
```

gnome-terminal --geometry 85x7+100+20

```

---

### Post by hictio on 2008-11-23
Another thing, I'm running Compiz, with the "Place window" plugin enabled on the CompizConfig Settings Manager, if you remove the XOFF & YOFF bit form the '--geometry' directive, it will honor the plugin's behaviour, or, well, at least, it is doing so with the one I'm using: "Cascade" placement.

But, if you add that, all the gnome-terminal windows will open on the same place disobeying the plugin's instructions, and, on top of that, all the windows will be one on top of each other.

---

### Post by graysky on 2008-11-23
> **hictio said:**
> Take a look at the man page of X, pretty likely you won't have it on an Ubuntu box, because it uses Xorg, I have take a peek at my FreeBSD box :D
]

Thanks dude, this is exactly what I wanted.

```
gnome-terminal --geometry 95x25+100+20
```

That gave a windows of 682x400 which is close enough :)

---

