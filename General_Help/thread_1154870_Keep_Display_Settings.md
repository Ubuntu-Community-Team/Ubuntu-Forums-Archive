---
title: "Keep Display Settings?"
date: 2009-05-10
forum: General Help
---

### Post by faustism on 2009-05-10
Hello,
I recently upgraded to 9.04 (and got a new monitor) and my display settings seem to reset themselves after i turn the computer off and on a couple of times.  Is there a way to make it so the settings don't auto-adjust (I'm guessing its detecting the monitor on start-up, but incorrectly)

Thanks in Advance

---

### Post by Legace on 2009-05-10
What display settings are you talking about?
Resolution? Vertical/Horizontal position?

---

### Post by faustism on 2009-05-10
the resolution and refresh rate.
the resolution is fine though.
When my computer turns on the refresh rate is set to 65 Hz and I want it at 80Hz. Even if i change it, the computer forgets the next time I start up

---

### Post by Legace on 2009-05-10
Go to [http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/) and get a Modeline.
For example:
```
Modeline  "1280x1024" 110.00 1280 1328 1512 1712 1024 1025 1028 1054
```

Now open Terminal, and type in:
```
sudo gedit /etc/X11/xorg.conf
```

Add YOUR modeline into the Monitor section. It will look something like this:
```
Section "Monitor"
	Identifier	"Configured Monitor"
        Modeline  "1280x1024" 110.00 1280 1328 1512 1712 1024 1025 1028 1054
EndSection
```

Then, in the Screen section, add your resolution (1280x1024 is an example, use your own resolution). It should look something like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
	Modes      "1280x1024"
	EndSubSection
EndSection
```

Finally save and reboot.

---

### Post by faustism on 2009-05-10
thanks. it seems to be working right now

---

