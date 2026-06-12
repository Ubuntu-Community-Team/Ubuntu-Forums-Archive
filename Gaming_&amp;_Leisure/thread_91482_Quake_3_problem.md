---
title: "Quake 3 problem"
date: 2005-11-17
forum: Gaming &amp; Leisure
---

### Post by Reducer on 2005-11-17
I've got Q3 and Q3:TA installed and running just fine on my Breezy system.  However, when I exit the program, my desktop is knocked back to 640x480, and I need to restart xorg to get it back to 1024x768.  Any ideas on that one?

Thanks.

---

### Post by snwcrash on 2005-11-18
I have the same problem, any ideas?

---

### Post by Ranime on 2005-11-19
You've got to "hard-lock" your resolution. You can do this by editing your xorg.conf file.

Open a terminal and backup your conf file first.
```
sudo cp /etc/X11/xorg.cond /etc/X11/xorg.conf_backup
```

After that, edit your conf file.
```
sudo gedit /etc/X11/xorg.conf
```

find this section:
```
...
Section "Screen"

```

Remove **all[/] colordepts en modes you're never gonna use [b]whitin the Section "Screen"**.
For example: My section "screen" is optimized for a 1152x864 (screensize) x24 bit (color) resolution. I removed all the other resolutions, sub sections and color dept variants.
```

...
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24	
	SubSection "Display"
		Depth		24
		Modes		"1152x864"
	EndSubSection
EndSection
...

```
When done, save the file and reboot your system (init 6). If all goes well you'll be looking at your desktop again. Play a game and exit it. You'll notice the resolution will be restored to your prefered setting.

If you've errored you'll end up with a X-server crash and you'll be thrown back in te TTY (terminal).

Login with your name and password.
Restore your conf file by typing this at the $
```

ranime@ishtar:~$ sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

when done, reboot your system:
```

ranime@ishtar:~$ sudo init 6

```

after the reboot, all your previous settings will be restored.:rolleyes:

---

### Post by Reducer on 2005-11-19
That worked for me.  Thanks!

---

