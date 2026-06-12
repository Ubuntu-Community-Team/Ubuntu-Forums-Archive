---
title: "Sloppy Graphics"
date: 2009-08-21
forum: Desktop Environments
---

### Post by jslick on 2009-08-21
I've had Kubuntu on my desktop for several months now and it worked fine.  Then, I played with the nvidia-settings overclocking and now my graphics are incredibly sloppy.  I did not save my settings so my card is at factory settings and is still sloppy.
Desktop effects are no longer smooth and games such as Globulation 2 play very poorly.
I am quite sure it is not my card because Globulation 2 runs like an athlete on my Windows XP.  I believe it is some configuration or driver that is screwed up in Kubuntu.
Is there a way to restore default configurations or fix my driver or other?

xorg.conf
```

#[...]
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	#Option	"Coolbits"	"1"
EndSection

```

Kubuntu 9.04
Nvidia GeForce 8500 GT

---

### Post by jslick on 2009-08-21
*ahem*
Anybody nobody how to fix suddenly sloppy graphics?

---

### Post by anthw27 on 2009-08-21
You could try, disabling the restricted driver and then re-enabling it.

Bump..anyone?

---

### Post by Dullstar on 2009-08-22
Hmm...  I've always found KDE a little confusing...  I just installed Kubuntu 8.04 in a VM just for testing things.

You could try ```
sudo apt-get install ubuntu-desktop
``` or ```
sudo apt-get install gnome
```...  or replace ubuntu/gnome with any other DE...  for testing purposes only, mainly...  I have my doubts that it's a DE problem though...   worth a try, though.

---

### Post by jslick on 2009-08-22
I finally fixed the problem.
I installed xfce to see if it was a KDE problem and that didn't fix the problem.

The problem turned out to be cpudyn, a frequency scaling daemon for Intel Speedstep.  I used to have Speedstep on, but I recently turned it off.  After I messed with my graphics clocks, I noticed problems; so, I really don't know what caused it.

But,```
sudo apt-get remove cpudyn
``` fixes the problem.
Cpudyn does not come with (K)ubuntu; I had installed it afterwards and it used to work with no problems.  For others with performance problems:  It is safe to uninstall cpudyn.

---

### Post by Dullstar on 2009-08-22
Like I said, I had my doubts about it being a KDE problem.

---

