---
title: "xsplash resolution"
date: 2010-04-06
forum: Desktop Environments
---

### Post by joebrueske on 2010-04-06
I think xsplash is pretty cool, and I've always enjoyed GDM. So having Xsplash before GDM, I thought was the best. Only problem I have is that Xsplash isn't using the same resolution as the desktop. Neither is GDM.

So, after I login, the resolution changes, and for about 3 seconds Xsplash looks fine. :) How do I fix this glitch?

---

### Post by Kakers on 2010-04-06
What files do you have in this directory?

"/usr/share/images/xsplash"

Is the problem with the sizes of the boxes or the background image?

---

### Post by joebrueske on 2010-04-06
> **Kakers said:**
> What files do you have in this directory?

"/usr/share/images/xsplash"

Is the problem with the sizes of the boxes or the background image?

Correct. For most people there's multiple resolutions. For me, there's just one. I'm wondering if that's because of my X11.conf file. Because I have video out on my laptop I have a virtual resolution and I don't have multiple "modes."
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2512 864
	EndSubSection
EndSection
```

---

