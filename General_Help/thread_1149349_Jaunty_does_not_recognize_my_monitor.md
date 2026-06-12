---
title: "Jaunty does not recognize my monitor"
date: 2009-05-05
forum: General Help
---

### Post by corrosion on 2009-05-05
Hi all,

Since it was not a problem for ubuntu since 8.04 to recognize my monitor (Samsung SyncMaster 2223NW) it seems it is a problem for Jaunty.
Ubuntu 9.04 (64bit) not only does NOT recognize the monitor but it doesn't give more than 1024x768.
I don't touch x.org files since 2 years ago (I changed gentoo for ubuntu) and it is surprising the resolution of the monitor is not a part of it.
So, what can I do? I was very comfortable not having to touch config files in my workstation...
Maybe an nvidia problem?

Well, thanks for your time and any help you can give!

---

### Post by dandnsmith on 2009-05-05
It sounds like you can see what is happening, so it would be possible to get to a terminal to execute

```
dpkg-reconfigure xserver-xorg
```

to get responses and feed in more appropriate detail in respect of your particular monitor

---

### Post by Legace on 2009-05-05
Do this (although this requires changing config files, this is completely safe)..

Open Terminal and type in:
```
sudo gedit /etc/X11/xorg.conf
```

Enter password, and press Enter.
A text editor window should open.

In the Screen secton of that file, add the following:
```

	SubSection "Display"
		Modes      "1440x900"
	EndSubSection
```

NOTE! Replace 1440x900 with your own resolution.

The end result should resemble this. Note that you may have slighty different format, but the most important things is that you have a subsection called display and your mode under it. :)

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes      "1440x900"
	EndSubSection
EndSection
```

Finally save (CTRL + S) and reboot. Try to set the resolution now using the Display tool found in System -> Preferences.

---

### Post by Irwin J. Finster on 2009-06-01
It seems I have the same problem, and I really don't like to mess around with the xorg.conf. I have tried to reinstall ubuntu and now have not activated the nvidia driver, but ubuntu by itself does not recognize my monitor ether. Is there a way to get ubuntu to see the right settings for my monitor? A monitor .inf file maybe? Or I seem to recall on some earilier versions of Ubuntu you could simply select your monitor from a big list?

---

### Post by Legace on 2009-06-01
> **Irwin J. Finster said:**
> A monitor .inf file maybe? Or I seem to recall on some earilier versions of Ubuntu you could simply select your monitor from a big list?

I'm afraid xorg.conf editing is the easiest way to solve your problem :/

---

### Post by mevan_snp on 2009-06-01
why is this vertion not supporting  monitors. lower vertion suppoert all the monitor? some one know the reson?

---

### Post by Legace on 2009-06-01
> **mevan_snp said:**
> why is this vertion not supporting  monitors. lower vertion suppoert all the monitor? some one know the reson?

I think its because the Display manager uses XRandr these days,,

---

### Post by Irwin J. Finster on 2009-06-01
This really sucks:( . I edited xorg.conf (see attachment) but this doesn't do anything.

---

### Post by mjm1231 on 2009-07-19
> **dandnsmith said:**
> It sounds like you can see what is happening, so it would be possible to get to a terminal to execute

```
dpkg-reconfigure xserver-xorg
```

to get responses and feed in more appropriate detail in respect of your particular monitor

I tried this approach. I was asked many questions about my keyboard, but none about my monitor, mouse, or video card.

---

