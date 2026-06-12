---
title: "CF Confusion... Can someone explain this?"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by amadeus266 on 2007-08-24
I have an ATI AIW 9200 and have had CF running near flawlessly until trevino's update on the 18th. I managed to get it working somewhat even after all that mess. This morning I installed the new updates and now I don't have window borders and a lot of the plugins are broken. The confusing part is this report from glxinfo...

```
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2
```


Tngsten Graphics??? I don't remember changing the driver and in my xorg.conf it still says:

```
Section "Device"
	Identifier	"ATI RADEON 9200"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection
```

This is what it has been since I installed Feisty when it was first released. Am I correct in assumng that  CF will no longer work on this machine? I can't even get Beryl running anymore.:confused:

---

### Post by jordanmthomas on 2007-08-24
You can maybe try this fix I found for my compiz problems:
[http://ubuntuforums.org/showthread.php?p=3244036#post3244036](http://ubuntuforums.org/showthread.php?p=3244036#post3244036)

It's worth a shot at least, and I was having problems after an update the other day and this fixed it.

---

### Post by amadeus266 on 2007-08-25
I never needed XGL before so I don't believe that I will need it now. I don't even get the normal desktop effects anymore. I guess it's time to reinstall.

---

### Post by jordanmthomas on 2007-08-25
I don't use XGL either, just AIGLX.  It's an issue that can affect both I think.

What is output if you try to run beryl in a terminal (fusion-icon or whatever it is you use)

---

### Post by amadeus266 on 2007-08-25
fusion-icon in terminal gives

```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```

I have decided that since I have nothing of importance on this machine that I am reinstalling from scratch. Thanks for your help anyway. I will just watch the forums to see when things are back to normal again with CF or wait until Gutsy is released. Until then, I will just make myself be happy with the default install of compiz. At least I'll have a cube and wobbly windows while my windows using friends will not and still be jealous.:guitar:


Edit: Some of my windows using friends have a cube and some effects... But they had to pay out the wazoo for them! LOL

---

