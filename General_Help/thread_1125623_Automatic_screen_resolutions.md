---
title: "Automatic screen resolutions"
date: 2009-04-14
forum: General Help
---

### Post by Peterph on 2009-04-14
I'm trying to set up a media computer and use my TV as the monitor but (K)ubuntu 8.10 and 9.04 seems to automatically try and identify screen resolution. In this case it defaults to 800x600 and I can't find out how to change it to a higher setting.

Is their any way of getting manual control back.

---

### Post by dabl on 2009-04-14
What happens when you go into KMenu>System Settings>Display and change the resolution?

Your graphics chip is the limiting item -- what is the manufacturer and model?

---

### Post by Peterph on 2009-04-14
I can choose between 800x600 and 640x480. I'm using a Nvidia 9500 and the proprietory drivers. It works fine on a standard monitor but not the TV. The TV was 1280x768 in 8.04.

I've looked xorg.conf. That's all it says.

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

dpkg-reconfigure lets me change the keyboard and nothing else.

---

### Post by 0xD4 on 2010-05-14
You can also try and call xrandr from one of the setup scripts.

---

