---
title: "How to tell if im running the correct vid driver"
date: 2006-09-20
forum: Desktop Environments
---

### Post by Brokenrgv on 2006-09-20
Just installed nvidia's driver from there website, would there be a command to check if its currently installed right,thanks.

---

### Post by lagagnon on 2006-09-20
lsmod and glxinfo.

---

### Post by kick6 on 2006-09-20
```
 glxinfo | grep direct
```

should return

```
 Direct Rendering: Yes
```

---

### Post by Brokenrgv on 2006-09-20
glxinfo returned 8774 somewhere in the readout so id say all's good, thanks for the help :)
ps Direct Rendering: Yes

Sorry one other question, how would one get the same refresh rates as seen in windows, im sitting on 85 mhtz currently yet in windows i could get 120 
would this come down to the drivers not allowing higher or is there something i could do to get the higher rates (better on the eyes):)

---

### Post by CatKiller on 2006-09-21
> **Brokenrgv said:**
> how would one get the same refresh rates as seen in windows, im sitting on 85 mhtz currently yet in windows i could get 120 
would this come down to the drivers not allowing higher or is there something i could do to get the higher rates

Find out the Horizontal Sync and Vertical Refresh ranges for your monitor, either from the manual or from the manufacturer's website. Then edit your xorg.conf file to reflect what your monitor is capable of:```
gksudo gedit /etc/X11/xorg.conf
``` find the Section "Monitor" part, and put in the HorizSync and VertRefresh values that you found earlier. For example, my xorg.conf file has this:
> Section "Monitor"
	Identifier	"Hansol 730E"
	Option		"DPMS"
	HorizSync	30-72
	VertRefresh	50-160
EndSection

HTH.

---

