---
title: "Annoyingly big letters on login screen"
date: 2009-06-06
forum: General Help
---

### Post by Dhananjaymb on 2009-06-06
on my jaunty system the letters on the login screen are annoyingly bigger. if I gets any Notifications on login manager only first two or three letters are visible.

---

### Post by Legace on 2009-06-06
> **Dhananjaymb said:**
> on my jaunty system the letters on the login screen are annoyingly bigger. if I gets any Notifications on login manager only first two or three letters are visible.

Open Terminal.
Type in:
```
sudo -i
```

Then type in password, and then:
```
gnome-display-properties
```

Make sure the resolution is right.

---

If that doesn't work after a reboot, type in the following into terminal:
```
sudo gedit /etc/X11/xorg.conf
```

and make sure the Screen section looks something like this (note, replace 1440x900 with you own, preferred resolution):
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes      "1440x900"
		Virtual	1440 900
	EndSubSection
EndSection
```

---

