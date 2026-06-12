---
title: "Change referesh rate on ViewSonic G810 and Intel i810 driver"
date: 2006-03-31
forum: Desktop Environments
---

### Post by s_baramov on 2006-03-31
This could be converted to HowTo, but I am not quite sure how to do it. 

Here is the problem: Fresh install of Kubuntu Breezy Badger (5.10). Run all of the updates. The vertical refresh rate is stuck on 60Hz for 1600x1200 and 1280x1024. The hardward is:

Video Controller: "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset
Monitor: ViewSonic G810

After brief research, I found out that my xorg.conf file does not have the right setting for Horizontal and Vertical refresh rates. Here are they as detected by Kubuntu install script: 

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60

According to the ViewSonic Web site [http://www.viewsonic.com/support/desktopdisplays/crtmonitors/graphicseries/g810/#specs](http://www.viewsonic.com/support/desktopdisplays/crtmonitors/graphicseries/g810/#specs) the refresh rates are different. So I changed them: 

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-97
	VertRefresh	50-180

Now, I can work on 1600x1200 on 75Hz and 1280x1024 on 85 Hz.

I hope someone can use this peace of info.

Stefan

---

