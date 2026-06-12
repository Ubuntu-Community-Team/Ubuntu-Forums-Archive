---
title: "Display resolution... set where?"
date: 2005-09-23
forum: Desktop Environments
---

### Post by offby1 on 2005-09-23
Okay...  I'm not a total n00b.  I know that the xorg.conf in /etc/X11 has a display configuration that includes the resolutions that the server will run at.  In my case, it looks like this:

```
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1600x1200"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection
```

Sooo....  This seems pretty straightforward -- I should get a 1600x1200 screen resolution, as there are no other possible sizes specified, right?

So why am I at 1280x1024, with options for 1152x864, 1024x768, 832x624, 800x600, and 640x480 in my screen resolution preferences dialog?  Where the hell does it get these values, and how the hell can I change them?

---

### Post by debian_n00b on 2005-09-24
All your basic desktop settings are right at your fingertips.
Under the main Gnome menu, do:
System -->> Preferences

---

### Post by offby1 on 2005-09-24
[QUOTE=debian_n00b]All your basic desktop settings are right at your fingertips.
Under the main Gnome menu, do:
System -->> Preferences[/QUOTE]

Please read the fine post and note that I cited a lack of the expected options *within the system preferences application for display resolution*.

---

### Post by FLeiXiuS on 2005-09-24
[QUOTE=offby1]Please read the fine post and note that I cited a lack of the expected options *within the system preferences application for display resolution*.[/QUOTE]

In the preference thing you should see "Screen Resolution".

---

### Post by debian_n00b on 2005-09-24
Sorry. Misread your post. Will look further.

---

### Post by offby1 on 2005-09-24
[QUOTE=FLeiXiuS]In the preference thing you should see "Screen Resolution".[/QUOTE]

And my issue is that the resolution I intend to use (And that I know both my display adaptor and monitor are capable of) does not show up in that preference panel.  I have typically run my display at 1600x1200 70Hz (although 65Hz is tolerable) and right now it's close -- the right resolution, but 60Hz only -- but I've already had the experience of the maximum resolution being 1280x1024, and this is with the above xorg.conf.

I *have* done my homework, here, to the extent that is possible.

On a slightly related note, why does Xorg not ship with the monitors file?  I'd love to get the exact right configuration for my monitor, but I'm not really sure where I'd go about digging that up, now.

---

### Post by FLeiXiuS on 2005-09-24
Under your monitor section in the xorg.conf, you should also define your horizontal sync frequencies along with your vertifical refresh rate.

```

Section "Monitor"
	Identifier	"Your Monitor Name"
	HorizSync	30-96
	VertRefresh	60
EndSection

```

These are examples for my monitor.  My monitor only supports 1600x1200 at 60hz so I suffer.  You can set the vertical refresh to multiple values by doing, #-#, (ex. 60-120)

That'll give you the option to select from a variety of commonly used refresh rates in the screen resolution menu.

Secondly, under the screen section you may want to define the resolutions you'd like to select from.
```

Section "Screen"
	Identifier	"Default Screen"
....
....
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

```

That should be everything.  Now you can select from a range of options!  Hope this solved your problem.

---

### Post by offby1 on 2005-09-24
The problem, there, is that those ARE set correctly, and are (sometimes) being ignored.  Specifically, they're fine for the first login, but if I log out and log back in again (still in GDM) the resolution settings I had are subsequently ignored.

This isn't a case of the common problems and missettings, or at least I hope not.

---

### Post by fordfan753 on 2005-09-24
Try to reconfigure the xserver
```
sudo dpkg-reconfigure xserver-xorg
``` 
And use the advanced method when you get to screen resolution. Make sure you have your monitor refresh specs handy, and only select the modes you want it to display. I can see that the xserver or maybe even GDM is ignoring your xorg.conf....have you tried turning down the depth to (ugh) 16bit, just to see what happens with your resolutions? Have you tried starting Gnome directly without using GDM? Oh, and you aren't using Breezy are you? The xserver in Breezy seems to be breaking a lot due to other upgrades, not that I think this would have much to do with this problem.

---

### Post by offby1 on 2005-09-25
I've tried all of those, and nothing works consistently.  What I suspect is happening is that the modes my monitor reports do not include the mode I run at, which is... kind of unsupported, although it has worked for me for three years without a hitch.

Anyway...

I suppose that a new monitor is in the cards eventually, anyway, but this is kind of silly -- it should just work! ;)

I'll keep on plugging.  At least I can give up on 3D -- the ATI drivers cause a hard hang in X if I, well, *use* them.  Bah.

---

