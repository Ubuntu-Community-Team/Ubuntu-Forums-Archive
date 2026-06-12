---
title: "X won't start: &quot;Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so&quot;"
date: 2007-01-13
forum: Desktop Environments
---

### Post by elreteipos on 2007-01-13
When I start X, it immediately shuts down again. *grep "EE" /var/log/Xorg.0.log* printed this text on the screen:> Current Operating System: Linux BETAubuntu 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
     (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
(II) Loading extension MIT-SCREEN-SAVERHow can I fix X?

---

### Post by scrooge_74 on 2007-01-13
Could be the drivers for your video card? Did you do any recent changes or updates?

do "sudo dpkg-reconfigure xserver-xorg"  and change the video driver either to what you are suppose to have or at least to VESA so you can have a GUI and fix the problem

---

### Post by elreteipos on 2007-01-14
> **scrooge_74 said:**
> Could be the drivers for your video card? Did you do any recent changes or updates?

do "sudo dpkg-reconfigure xserver-xorg"  and change the video driver either to what you are suppose to have or at least to VESA so you can have a GUI and fix the problem
I tried reconfiguring xserver. However, I forgot to select the VESA driver. I accepted all autodetected settings, and of course it still didn't work. Then I tried starting the configuration tool again, but Ubuntu claims that it is not installed anymore! So I did *sudo apt-get install xserver-xorg*, but then Ubuntu said that it **is** installed! What should I do now?

---

### Post by scrooge_74 on 2007-01-14
log in again reconfigure the server, you should in any case be able to get back into command line when you boot, if not after boot try CTRL+ALT+F1

and then log in

---

### Post by elreteipos on 2007-01-15
I changed the driver to VESA, but the same thing keeps happening over and over again. *grep "EE" /var/log/Xorg.0.log* returned this:> Current Operating System: Linux BETAubuntu 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

---

### Post by scrooge_74 on 2007-01-15
check you have some wacom device trying to work, I myself get some misterious problem using the little buttom that serves as my mouse in the middle of the keyboard and get a similar error message

---

### Post by elreteipos on 2007-01-16
> check you have some wacom device trying to workUh? Can you explain what a wacom device is please?

---

### Post by scrooge_74 on 2007-01-16
i was checking on the net and WACOM devices are for managing tablet screens and their pens

---

### Post by Cuddles on 2007-01-22
i have had a similar problem with xorg not starting because of glcore, however, it starts with startx on command line, which confuses me very much, im thinking disabling the glcore module would probably solve my problem, the wacom devices are for tablet pc's, and can be rem'd out of the xorg.conf file w/o damage, which should resolve the errors with wacom....i cannot get my system to boot into the login screen, but loging in by command line and using startx starts gdm fine....it seems to me as though glcore has problems with the sis driver, although i had it running at one point, it now seems to fail....i have some 3d standalone projects that still seem to run perfectly, which they would not before i installed the glcore modules...again, my problem is apparently only during bootup, this is why i cannot figure out the cause....i made a backup of my custom configuration and used the autoconfiguration script, and it added a bunch of wacom stuff, at which point it still did not boot normally, but startx still worked (had to delete the .X0-lock file first, as ctrl+alt+backspace to get out of the frozen attempt to start xorg at bootup doesnt seem to get rid of it, but as soon as i had, it ran flawlessly....im curious if this is merely a login prompt problem)

sorry for the long, relatively unseparated post, but im a bit tired and i have a headache....

---

### Post by elreteipos on 2007-01-23
A few days ago, I decided to reinstall Ubuntu. Everything's working fine now. :)

---

