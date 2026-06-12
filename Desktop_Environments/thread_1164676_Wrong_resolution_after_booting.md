---
title: "Wrong resolution after booting"
date: 2009-05-19
forum: Desktop Environments
---

### Post by Quarterpipesmoker on 2009-05-19
At booting kdm starts with a higher resolution (1280x...). If I then restart the x-server the right resolution (1024x...) is used.

Edit: Happens not everytime. Are there some configuration files, where I could look?

---

### Post by Quarterpipesmoker on 2009-05-21
Nothing to find in
/etc/X11/xorg.conf

My system seems to use wrong parameters (frequencies).

The proposal in
[http://ubuntuforums.org/showthread.php?t=313072](http://ubuntuforums.org/showthread.php?t=313072)
didn't help and 'dpkg-reconfigure' just cared about my keyboard setting...

---

### Post by Quarterpipesmoker on 2009-05-25
[s]Still starting with the wrong resolution. Next try is adding the resolution into xorg.conf... still waiting for someone to help. The changed part of the xorg.conf:[/s]

```
[s]Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
EndSection

Section "Monitor"
	Identifier	"Samtron 76Bdf"
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	50-160
	Modes		"1024x768"
EndSection[/s]
```

Edit: Don't do it at home... :) Changing the xorg.conf in the way I did, caused kdm to not start, because of wrong mode setting, so I had to edit the xorg.conf in the console and 'startx' manually.


But I think this try will end like before, because (k)ubuntu 9.* seems to ignore the xorg.conf and a ubuntu (different pc) also doesn't provide the screen resolution change tool anymore since dist-upgrade... HELP!

---

### Post by skyjacker on 2009-05-25
> **Quarterpipesmoker said:**
> At booting kdm starts with a higher resolution (1280x...). If I then restart the x-server the right resolution (1024x...) is used.

Edit: Happens not everytime. Are there some configuration files, where I could look?
Left click on the application launcher. 
Left click "Applications"
Left click "System".
Left click "Screen resize & Rotate"
Look for a Blue computer screen to appear in the "System Tray"
Right click on this and choose the resolution you need.... Good Luck

---

### Post by Quarterpipesmoker on 2009-05-26
Thx @skyjacker, but if I start with the wrong resolution, my task bar is at the wrong resolution, so restarting the x-server is still the only solution. Wether at kdm or with Alt + Supersondertaste (SysRq) + K

Booting from the very beginning starts with a certain solution and kdm/xorg don't change it. Thats the reason. Now, again: How do I change that?

---

### Post by Quarterpipesmoker on 2009-07-03
up

---

