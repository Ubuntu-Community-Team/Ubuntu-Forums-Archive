---
title: "Raise/Focus Problem"
date: 2007-11-14
forum: Desktop Effects &amp; Customization
---

### Post by open_coder on 2007-11-14
Okay, I am running Kubuntu 7.10. I installed Compiz fusion and have everything basically the way I want it. However, When I try to set the raise option so that Windows raise on a click. the setting doesnt stay. 

Does anybody else have this problem. I just want to have raise on click. 

Thanks for the help.

--Alex

---

### Post by battlesound on 2008-01-08
Yup... same here.  I've gotten it to work on a laptop using the gl desktop installed from "compiz-gnome".

Did you fix this problem, yet???

---

### Post by battlesound on 2008-01-09
Okay, I think I got it.  It's working now, anyway.  

**First of all, Ensure that the "Opacify" plugin is not checked in the CCSM (compiz config setings manager)!!  That should do it.  Otherwise, read and do the following below, and then leave that plugin unchecked.**

This is assuming you have an Nvidia graphics card in your system.  On the computer in question for me, I have an Nvidia Geforce 8600 GT.  If you have an Intel card or ATI card click on the appropriate link at the top left on the Compiz documentation site [http://www.compiz.org/Documentation/Documentation]("http://www.compiz.org/Documentation/Documentation") and ensure the xorg.conf file is the way they want it!

You need to edit your /etc/X11/**xorg.conf** file, and then install Compiz.

So use the Synaptic Package Manager (under system>admin), search for **compiz** and uninstall all of your compiz packages.

**Now, edit the xorg.conf file as per the compiz.org documentation page for Nvidia cards:**

The hard way is editing your xorg.conf file manually, but it isn't that hard. First type this into a terminal:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo gedit /etc/X11/xorg.conf
```

Find this section:

```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	...
	Load	"type1"
	Load	"vbe"
EndSection
```

Comment out dri and GLcore (if present), like this:

```
#	Load	"dri"
#	Load	"GLcore"
```

Make sure the glx module is loaded, like this:

```
Load	"glx"
```

Make sure the X11 extmod will load:

```
Load       "extmod"
```

Find this section (your values may vary) :

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection
```

Make sure DefaultDepth is set to 24, if it isn't already, then add the following lines below "EndSubSection" or above the first "SubSection"

```
Option         "AddARGBGLXVisuals" "true"
Option         "DisableGLXRootClipping" "true"
```

Add this to the very end:

```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Save the file and exit the text editor. Now restart the X-server by pressing Ctrl+Alt+Backspace or reboot. After this you're ready to install Compiz!

Great!  So now install all the typical compiz things using Synaptic, reboot, and then configure things using ccsm (compiz config settings manager), and ensure that you don't check the "Opacify" plugin.  That should do it.

Also.  Install Emerald Themer from the repos, and then you can get all the emerald themes from the fiesty repo list from here:
[http://packages.ubuntu.com/feisty/x11/emerald-themes]("http://packages.ubuntu.com/feisty/x11/emerald-themes")
Then, go to CCSM again, click on the "Window Decoration" plugin, and ensure that the **Command** line reads:
```
emerald --replace
```

---

