---
title: "Monitor Calibration"
date: 2010-04-17
forum: Desktop Environments
---

### Post by buck2825 on 2010-04-17
I am into digital photography.  So I needed to calibrate my monitor for when I have things printed or published so the color is what I intended.

Below is a very well written how to.


[http://www.linux.com/archive/feature/113936](http://www.linux.com/archive/feature/113936)


in short download the gamma charts.  from a distance or while burring your vision find the point on the chart where horizontal line blends with the gray background.  this is your current Gamma setting. the Ideal Gamma is 2.2.  (you might want to do some test prints)

use ```
xgamma -gamma x.xx
```

to multiply by a correction factor.  mess with this until you read 2.2

to make this happen every time you boot create a file /etc/X11/xorg.conf

ctrl-alt-F1
log in
```
sudo /etc/init.d/gdm stop
sudo X -configure
sudo /etc/init.d/gdm start
exit
```
ctrl-alt-F7

this will make a xorg.conf.new file in your home dir.
edit and rename that and move it to /etc/X11/xorg.conf 
(mind your permissions)


in you xorg.conf file edit as below 

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	**Gamma 0.83 0.80 0.80**
EndSection

red = 0.83
green = 0.80
blue = 0.80

restart X (alt-prnt scrn-k)

to edit each channel individually 


```
xgamma -rgamma 0.83
xgamma -ggamma 0.80
xgamma -bgamma 0.80
```

---

### Post by pooya72 on 2010-06-06
Thanks, I was looking for something like this. I wish there was a way to upvote helpful posts :KS

---

