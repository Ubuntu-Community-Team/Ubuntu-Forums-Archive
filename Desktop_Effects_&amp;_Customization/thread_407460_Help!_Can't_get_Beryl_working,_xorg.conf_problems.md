---
title: "Help! Can't get Beryl working, xorg.conf problems?"
date: 2007-04-12
forum: Desktop Effects &amp; Customization
---

### Post by ChrisUK on 2007-04-12
Hi all.

I am new to Ubuntu and have been desperately trying to get Beryl/AIGLX (Nvidia) working on my Ubuntu, but with no luck.

I was basically following this guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

And all was going well until I got to the part where it asked me to edit my xorg.conf file, here is what it asks:

>     * Add this to xorg.conf "Screen" section 

# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Option "DisableGLXRootClipping" "True"

    * Add this to xorg.conf "Device" section 

Option          "TripleBuffer" "true"

    * Restart X with ctrl+alt+backspace 

As soon as I add those bits to the Device and Screen section, then restart the X server, my screen goes black for a few seconds, then I get a blue screen saying something like "Failed to start X server, it is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem".
So I need to restart my PC, and after it gets passed the Ubuntu loading screen, it gets to an ugly looking black login screen.
So I need to login and use the backed up xorg.conf file that I luckily backed up before making the changes.

Beryl does seem to be installed and I see the red gem icon in the top right, I can right click on it and see the options, but the "Window manager" is basically stuck on "Metacity" (default) and when I try to change it to "Beryl" my windows flicker for a second or so and nothing happeneds, it's back to "Metacity" again - so clearly something is wrong.

I can't seem to get passed this xorg.conf instruction without causing the X server to fail...

Here is what my Device and Screen section looks like as default:

> Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

> Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection


Can anyone help?
It's giving me a huge headache and I've spent hours trying to fix it!
I don't know if it could be something to do with my nvidia drivers - I don't even know which drivers I have installed! :( :( :(

EDIT: I just typed "beryl" into terminal and got the following, just incase it helps diagnose anything:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
Xlib:  extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

### Post by Valstorm2323 on 2007-04-12
Sounds like your vid card didn't have a proper nvidia driver installed to me.

Try this site>

[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html)


What make/model is your nvidia?

---

### Post by ChrisUK on 2007-04-12
> **Valstorm2323 said:**
> Sounds like your vid card didn't have a proper nvidia driver installed to me.

Try this site>

[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html)


What make/model is your nvidia?

Thanks.
It's a Nvidia 7900GS (It's a Dell laptop).

---

### Post by dreadlord_chris on 2007-04-12
You need to set the **DefaultDepth** in the _Screen_ section to 24. 3d & compositing effects just don't work at lower then 24bit color...

---

### Post by ChrisUK on 2007-04-13
> **Valstorm2323 said:**
> Sounds like your vid card didn't have a proper nvidia driver installed to me.

Try this site>

[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html)


What make/model is your nvidia?

You were right... I thought the driver was installed but it turns out it wasn't.
The driver has now been installed correctly and Beryl is working. however it does seem quite laggy when shrinking windows, etc. Spinning the cube and grabbing/moving windows seems OK, it's when I minimize windows it seems to be quite laggy, and scrolling. It's not my PC because it's very high spec.
How do I disable the thumbnail windows when I put me mouse over minimized windows?

Also, I just typed "Beryl" into terminal and get the following: 

> Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 147 requests (144 known processed) with 0 events remaining.


---

### Post by bdogg64 on 2007-04-13
> **ChrisUK said:**
> You were right... I thought the driver was installed but it turns out it wasn't.
The driver has now been installed correctly and Beryl is working. however it does seem quite laggy when shrinking windows, etc. Spinning the cube and grabbing/moving windows seems OK, it's when I minimize windows it seems to be quite laggy, and scrolling. It's not my PC because it's very high spec.
How do I disable the thumbnail windows when I put me mouse over minimized windows?

Also, I just typed "Beryl" into terminal and get the following:

try

```
beryl --use-copy
```

---

### Post by ChrisUK on 2007-04-13
> **bdogg64 said:**
> try

```
beryl --use-copy
```

It said: 
> Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 147 requests (144 known processed) with 0 events remaining.


All the others passed OK.

I have figured out how to disable thumbnails by the way.
I think the laggy windows, etc. could possibly be my graphics drivers because I have only just installed them - it's hard to know for sure.

---

