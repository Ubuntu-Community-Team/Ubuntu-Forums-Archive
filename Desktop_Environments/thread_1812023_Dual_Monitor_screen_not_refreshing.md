---
title: "Dual Monitor screen not refreshing"
date: 2011-07-25
forum: Desktop Environments
---

### Post by mrblue182 on 2011-07-25
I have a dual monitor set up with an ATI card. The background of my main monitor (the right one) does not refresh. Meaning when I minimize to desktop, the windows still look like they're up (think frozen windows in windows 98). [Screenshot.]("http://i.imgur.com/Cp7ov.png")

Here is my xorg.conf if it is useful.
> 
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2720 1024
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection


Thanks in advance.

---

### Post by inspiral on 2012-03-23
Hi

Did you fix this ? 

I've got the same problem on the second ie. non primary screen. The only way I can fix it is turn it off/on via the '"Displays" setting window.

fyi I'm using a recent ATI graphics card.

Cheers

---

