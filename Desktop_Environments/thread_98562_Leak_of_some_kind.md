---
title: "Leak of some kind?"
date: 2005-12-03
forum: Desktop Environments
---

### Post by rozojc on 2005-12-03
Hi every1,

I've been using Breezy for a couple of months now, everything's great. I have, however, one slight problem. Recently (maybe since last kernel upgrade, buy I'm not sure) I have been experiencing some kind of processor leak...

Everything's working fine, but after a couple of hours or so I the system starts using the processor at 100%... I checked the system monitor, but no process seems to be using the processor... I closed all the windows in Gnome, waited a few minutes and nothing changed, it continued using the processor at 100%...


How can I check what is using the system's resources? (Other than System Monitor cause it doesn't list anything in "Processes"). Better still, how can I fix this?


Thanx

---

### Post by invalid on 2005-12-03
Use a terminal and type```
top
```

Cheers,
Cb

---

### Post by rozojc on 2005-12-03
[QUOTE=invalid]Use a terminal and type```
top
```

Cheers,
Cb[/QUOTE]
Hmmm, I just did that and the process that seems to be using the whole processor is actually Xorg !!!!

If I kill that wouldn't I be left in the terminal or something???? What can I do?

Edit:
Ok, I tried killing the process, it took me to the terminal and auto re started gnome. Then everything was fine... Does somebody know how I can fix this for good? I mean, it is happening each couple of hours so I guess there's a solution, right?

---

### Post by DrBair on 2005-12-03
What video driver are you currently using?  If you are unsure open /etc/X11/xorg.conf with your favorite editor and look in the 'Device' section.

---

### Post by rozojc on 2005-12-03
[QUOTE=DrBair]What video driver are you currently using?  If you are unsure open /etc/X11/xorg.conf with your favorite editor and look in the 'Device' section.[/QUOTE]

Well, its an Acer 3003LCi laptop, en the file you say I found this (I guess this is what you mean, I think...)

Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) SiS Default Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Any ideas?

---

