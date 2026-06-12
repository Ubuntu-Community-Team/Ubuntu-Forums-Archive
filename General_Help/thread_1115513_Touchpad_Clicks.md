---
title: "Touchpad Clicks"
date: 2009-04-03
forum: General Help
---

### Post by RedSingularity on 2009-04-03
Is there any way to disable touchpad clicking?  I dont have the option to do so under the "mouse" settings.

---

### Post by paradigm2 on 2009-04-03
> **Shadow121 said:**
> Is there any way to disable touchpad clicking?  I dont have the option to do so under the "mouse" settings.

You don't have that option for sure?  System -> PReferences -> Mouse -> Touchpad If I recall it might have been hidden under a tab which says "Touchpad".  Do you see that at all?  Then after hitting touchpad, you should see it.  I'm not on my laptop now to say for sure but remember disabling it on mine.  I almost missed it myself.

---

### Post by ShaunG on 2009-04-03
Yes.

You can do it by editing /etc/X11/xorg.conf

I suggest you backup xorg.conf first though.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then 

```
sudo gedit /etc/X11/xorg.conf
```

There should be a section in there similar to the following:

> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Add the following line to the end of the list of options.

> 	Option		"MaxTapTime"	"0"

Now restart X, (by loging out then log back in) and hopefully touchpad clicking is disabled. :)

Hope this helps

---

### Post by RedSingularity on 2009-04-03
Its not made by synaptic.  Its a netbook with a Sentelic touchpad.

---

### Post by ShaunG on 2009-04-04
Apologies I didn't know.

I am unfamiliar with Sentelic sorry. :(

---

### Post by RedSingularity on 2009-04-04
Yeah i think most people are not familiar......I dont know why they had to use this stupid pad.  Idiots should have stuck with synaptic!

---

### Post by ShaunG on 2009-04-04
They really should have. After a bit of googling, it would seem there are problems with drivers for the Sentelic touchpad and that there is a request for touchpad tap disable. I may have read it wrong (37th hour of no sleep)

---

