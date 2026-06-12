---
title: "[SOLVED] Xsettings"
date: 2007-11-12
forum: Desktop Environments
---

### Post by jagannath on 2007-11-12
Every time I start my Ubuntu Gutsy, I get the message asking me if I want to use " X settings" or use "Previous Gnome settings" as my keyboard settngs. This was not happening before. This has started after I installed xserver-xgl and then uninstalled it.
Could someone tell me why I am getting this and how I can stop this??

Hope I am posting in the right forum.:-?

Thanks,

---
J

---

### Post by erfahren on 2007-11-12
that message isn't very clear is it? I've dealt with it a number of times and am still not quite clear on it. 
anyway this may help, see: [http://ubuntuforums.org/showthread.php?t=576662](http://ubuntuforums.org/showthread.php?t=576662)

---

### Post by jagannath on 2007-11-12
I am attaching a screenshot of what I get. 

I followed the suggested link alright, but that does not seem to help.

---

### Post by erfahren on 2007-11-12
there's also this thread: [http://ubuntuforums.org/showthread.php?t=405274](http://ubuntuforums.org/showthread.php?t=405274)
the last post  suggests just going to System > Preferences > Keyboard and under Layouts check the Default button (or maybe "Reset Defaults")

not sure what kind of keyboard you have but did a google search on "  model "pc105", layout "us" and option "lv3  "

came up with [this page](http://www.knowprose.com/node/2394) and under the keyboard topic it says: "The lv3:switch option is only for keyboard layouts that require a 3rd level of shift (that is
, one more than the normal shift keys)."

so if you have a keyboard like that you would want that option. check out the keyboard preferences and see what options are available. If you have a keyboard like that you might want to research it more.

---

### Post by jagannath on 2007-11-12
Thanks erfahren 
Looks like this is going to take some time tofigure out. 
Anyway this is only a minor irritant. I'll try and work this out patiently.

---
J

---

### Post by jagannath on 2007-11-14
The problem got solved miraculously, it would seem. 
I suspect it was commenting out the lines ( in the keyboard section of xorg.conf)  as below that sorted things out.

        # Option		"XkbLayout"	"us"
	# Option		"XkbOptions"	"lv3:ralt_switch"
Thanks again erfahren for pointing me in the right direction.

-----
J

---

