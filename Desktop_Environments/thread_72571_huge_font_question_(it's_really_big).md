---
title: "huge font question (it's really big)"
date: 2005-10-06
forum: Desktop Environments
---

### Post by 11hjpphty76lkjj on 2005-10-06
Hey all.  Quick question...

so when I'm in thunderbird the fonts are all the correct size, but when I run Quanta the fonts are huge, like 18-20 vs. the normal 10-14.  I've checked the System>Pref>Fonts and it's set correctly, I've tried restarting gdm same thing.  Using Hoary...any ideas?

Thanks!

Aaron

---

### Post by Dolphin on 2005-10-06
open a console

enter
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```

In your xorg.conf, look for Section "Monitor" and insert these lines:

```
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	370	# 1600x1400 96dpi
```

Uncomment the line coresponding to the resolution you're using.
Restart X.

---

### Post by darkmatter on 2005-10-06
[QUOTE=kalosaurusrex]Hey all.  Quick question...

so when I'm in thunderbird the fonts are all the correct size, but when I run Quanta the fonts are huge, like 18-20 vs. the normal 10-14.  I've checked the System>Pref>Fonts and it's set correctly, I've tried restarting gdm same thing.  Using Hoary...any ideas?

Thanks!

Aaron[/QUOTE]

Quanta is a QT app. You need to install qt3-qtconfig, this will allow you to change the settings

Here's a link to the How-To
[http://www.ubuntuforums.org/showthread.php?t=56630](http://www.ubuntuforums.org/showthread.php?t=56630)

---

### Post by 11hjpphty76lkjj on 2005-10-07
I tried both of these to no avail.  I installed qt3-config, but how to I run it to configure it?

Aaron

---

### Post by darkmatter on 2005-10-07
Right click on the desktop and open a terminal, enter the following command

```
qtconfig
```

you will be presented by an interface through which you can change the setting.

---

### Post by 11hjpphty76lkjj on 2005-10-07
I tried that..still no work..here are some screenshots of my settings.

This one is the qtconfig setup

[IMG]http://www.kalosaurusrex.com/screenshots/qtconfig.png[/IMG]

here is what quanta looks like..

[IMG]http://www.kalosaurusrex.com/screenshots/quanta.png[/IMG]

here is my ubuntu fonts setup.

[IMG]http://www.kalosaurusrex.com/screenshots/ubuntufonts.png[/IMG]

I changed qtconfig then restarted gdm.  Same issue.  The quanta fonts are out of control.  bad fonts bad!

Aaron

---

### Post by darkmatter on 2005-10-07
Hmmm...

Perhaps installing kcontrol (KDE's control center) would allow you to fix the issue with the fonts in Quanta. 

If qtconfig isn't fixing the problem, it is the only other option I can think of at the moment.(Hey, I can't help it if I just woke up.;) )

Anyway, keep me posted. I'll see if I can come up with anything else.

---

### Post by 11hjpphty76lkjj on 2005-10-07
That did the trick!!!  Thanks for the help!

Aaron

---

### Post by jcollins on 2008-01-15
I have the same problem. This is definitely the problem because my screen size is reported to be 289x21 milimiters. I think this is also causing my video to look smashed in Totem.

I have set the value in my xorg.conf to what it should be. It is just not picking it up.

Here is my monitor section:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	DisplaySize	330 206
EndSection
```

"xdpyinfo | grep dimension" returns:
```
dimensions:    1280x800 pixels (289x21 millimeters)
```
"xrandr --query" returns:
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right)
LVDS connected 1280x800+0+0 (normal left inverted right) 289mm x 21mm
   1280x800       60.1*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)
```

---

