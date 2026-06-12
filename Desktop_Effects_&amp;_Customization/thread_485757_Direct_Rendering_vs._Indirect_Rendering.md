---
title: "Direct Rendering vs. Indirect Rendering"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by nunnst on 2007-06-27
First, Compiz 0.5.1 is running pretty nicely under Ubuntu Feisty on laptop (not sure how this happened, being the noob I am!).  What I can't figure out is how to implement direct rendering instead of indirect rendering.  It seems to me that direct rendering would have significant performance advantages.

I have an HP dv8210 w/ ATI Radeon Xpress 200M integrated graphics chip-set (128MB sideport memory setup as sideport only).

The command:

```
glxinfo | grep direct
```

Returns:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
```

My xorg.conf is:

```
Section "Device"
	Identifier  "ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1440x900"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```


**[color=darkred]How do I implement direct rendering?[/color]**  I have searched and searched the ubuntu forums and the WWW with no success.  Any help would be appreciated.

I'm hoping direct rendering will improve some of the choppiness I experience when scrolling in a window (firefox mainly).  Also, some of my apps don't seem to repaint well when scrolling under Xgl.  

Thanks in advance.

Steve

---

### Post by hansie99 on 2007-06-28
Hi Steve,

I had the same question (and some problems with Compiz, see [http://ubuntuforums.org/showthread.php?t=486754](http://ubuntuforums.org/showthread.php?t=486754) ) , only I use Dapper. 

I think that you have Compiz (or Beryl,etc.) and indirect rendering 

*or*

direct rendering and no Compiz. 

Both would be very great, since using Compiz slows down video very much, but the fora I've read point to the conclusion that both isn't possible. I don 't understand exactly why this isn't possible in theory. Perhaps someone here can explain? 

Bye,
Hans

---

### Post by FuturePilot on 2007-06-28
It is possible to have direct rendering and Beryl. I'm using Beryl right now and have direct rendering.
Towards the top of your xorg.conf file there should be a section called Module
Just add ```
Load             "dri"
```
That should give you direct rendering.
I have a Nvidia card not sure if it makes a difference. I haven't noticed a difference in performance with or without it.

---

### Post by Topfs on 2007-06-28
Shouldn't the tag Composite at the end be enabled? isn't that direct rendering?

It is in my xorg.conf but I have a Nvidia card (Bless them on linux)

Snippet from my Xorg.conf
```

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by hansie99 on 2007-06-28
FuturePilot, I have Load "dri"  in my xorg.conf but no direct rendering. Any other ideas? 

Also, if I understand correctly,  

Option "Composite" should be "false"  when using Beryl/Compiz. 

This option is only set to "true" if you are using xcompmgr

---

### Post by Steveway on 2007-06-28
That's not a bug.
This is by design, XGLs Design.
XGL "steals" your direct rendering. Why?
Well, XGL is basically a fullscreen OpenGL app, and having direct rendering inside an OpenGL app is afaik not possible.

---

### Post by Topfs on 2007-06-28
I have compiz Fusion up and running on that xorg.conf. And it runs flawlessly. Have crashed once since install.
Alot better than the first months with beryl :)

---

### Post by FuturePilot on 2007-06-28
> **Steveway said:**
> That's not a bug.
This is by design, XGLs Design.
XGL "steals" your direct rendering. Why?
Well, XGL is basically a fullscreen OpenGL app, and having direct rendering inside an OpenGL app is afaik not possible.

Ah, that's why. Wasn't aware the OP was using XGL. You can't have direct rendering with XGL. As for the Composite Extension it needs to be enabled if you're using Nvidia for Beryl. That's one of the main things Beryl needs. After all Beryl is a Compositor.

---

### Post by acadiansteph on 2007-06-29
I used this guide to get direct rendering with my ATI card ,here is the URL: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) .Rembember with this guide you will get 3d graphics acceleration but the Composite extension will be disabled (i.e. no chance for deskop effects). Hope this helps

---

### Post by acadiansteph on 2007-06-29
By the way , I have the same 200m ATI card. Just follow the guide step by step. Then you should have 3d graphics acceleration. Try it with GLMatrix screensaver, you will see it is cool!!! Best of luck;)

---

### Post by nunnst on 2007-06-29
Thanks to all for your responses.  Seems like compiz is just not yet ready for direct rendering to the Graphics Processing Unit.  I will continue to use it to "show-off" but until it becomes less CPU intensive I will not use it on a day-to-day basis.

Damn, I really wanted to shove it in the faces of Vista users, lol.

---

