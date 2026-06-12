---
title: "can't get direct rendering"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by dr.silly on 2007-04-26
ok I have a geforce 2 and i don't have 3d acceleration but I know my card's good enough because [robot arena]("http://youtube.com/watch?v=8KNUiEtgyic") works like a charm in windows it's just that it's not configured correctly in ubuntu. I installed and enable the nvidia-glx-legacy package but that didn't work. I  want to get the special effects working that come with 7.04

---

### Post by dr.silly on 2007-04-28
should I just get a new graphics card off ebay?

---

### Post by dcstar on 2007-04-29
> **dr.silly said:**
> ok I have a geforce 2 and i don't have 3d acceleration but I know my card's good enough because [robot arena]("http://youtube.com/watch?v=8KNUiEtgyic") works like a charm in windows it's just that it's not configured correctly in ubuntu. I installed and enable the nvidia-glx-legacy package but that didn't work. I  want to get the special effects working that come with 7.04

Try adding the highlighted line to the appropriate place in your /etc/X11/xorg.conf file:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"BenQ FP92W"
	DefaultDepth	24
**	Option		"AllowGLXWithComposite" "1"**

```

---

### Post by dr.silly on 2007-04-29
Thank You!!!

---

### Post by dr.silly on 2007-04-29
ok direct rendering works but when I enable desktop effects all the windows lose their title bars and borders and then nothing happens

---

### Post by dr.silly on 2007-04-29
should I installl xgl + beryl manually?

---

