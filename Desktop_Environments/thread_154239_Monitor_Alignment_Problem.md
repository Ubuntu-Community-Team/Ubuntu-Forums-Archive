---
title: "Monitor Alignment Problem"
date: 2006-04-02
forum: Desktop Environments
---

### Post by GiantsFanMan11 on 2006-04-02
I am having some problems with aligning my monitor.  The screen is shifted a little to the right so I run xvidtune and shift the screen to where it fits.  Then I edit xorg.conf like so:

```
Section "Monitor"
Identifier	"Generic Monitor"
HorizSync 30.00 - 80.00
VertRefresh 56.00 - 76.00
Modeline "1280x1024" 135.00 1280 1312 1456 1688 1024 1025 1028 1066 + hsync + vsync
```

But, when I restart my computer, the monitor goes right back to the way it was.  The xorg.conf file keeps the changes, so I'm not sure what is going wrong.

There is also a Section "Screen" in xorg.conf.  Could something in there be countering the changes I have made?  Thanks.
Steve

---

### Post by GiantsFanMan11 on 2006-04-15
Never mind.  It seems to work now for reasons that are beyond me.:-k

---

### Post by Nikusan on 2006-10-28
Similar problem here after a dist-upgrade from dapper to edgy. Doing a dpkg-reconfigure xserver-xorg fixed it at the login screen but it jumped back over to the right after logging in.

---

### Post by sylvester_0 on 2006-10-28
Strange. The resolution should be the same between login screen and desktop. This is a CRT I assume? LCDs should auto adjust to any changes as such. If you're talking about the bootsplash, I wouldn't be too concerned if it isn't lined up properly.

---

### Post by mistypotato on 2006-12-31
Same problem here.....

screen is shifted to the right slightly.

About 1/4 - 1/2 inch.

This was after a virgin install immediately after installation so it is default behavior.

anyone know how to correct this?

Thanks

---

### Post by Ozdemon on 2007-07-03
> **mistypotato said:**
> Same problem here.....

screen is shifted to the right slightly.

About 1/4 - 1/2 inch.

This was after a virgin install immediately after installation so it is default behavior.

anyone know how to correct this?

Thanks

Same problem here.  Just installed Ubuntu.  Anyone find a fix?

**Update**
Problem fixed by using automatix to update nvidia driver

---

