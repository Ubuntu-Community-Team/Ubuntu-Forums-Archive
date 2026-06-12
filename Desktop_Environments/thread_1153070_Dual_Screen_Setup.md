---
title: "Dual Screen Setup"
date: 2009-05-08
forum: Desktop Environments
---

### Post by duffboy on 2009-05-08
I am currently running Intrepid on a Dell Inspiron 710m. I am trying to correctly configure my dual monitors.

I am trying to configure my 19" 2nd monitor rotated and to be located on the left of my laptop's main screen.

The screens come up the right size, but my 2nd monitor is not rotated. I have to use the randr every time I boot to move my 2nd monitor to the left of my main monitor and rotate it to the left.

If someone could provide some guidance that would be great. Thanks.

I have included my xorg.conf.

```

Section "Device"
	Identifier	"Configured Video Device"
        Option          "monitor-LVDS" "Configured Monitor"
	Option          "monitor-VGA" "19Monitor"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Option "PreferredMode"  "1280x800"
        Option "Position" "900 0"
EndSection

Section "Monitor"
        Identifier      "19Monitor"
	Option "PreferredMode"  "900x1440"
	Option "Position" "0 0"
        Option "LeftOf" "Configured Monitor"
        Option "Enable"  "true"
    	Option "Rotate"  "left"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2180 2240
	EndSubSection
EndSection

```

---

### Post by Kareeser on 2009-05-08
The 710m? With the white keys? Lucky you... I bought the 700m.

Is there any reason you can't put those commands into a script and set it to run on system start?

---

### Post by duffboy on 2009-05-11
I could put it into a script. I feel as though I would not be winning this battle though.

I am trying to figure out the proper way to establish the monitors in xorg. I am a fairly recent convert from windows and was always very frustrated having to have a number of batches run right at my win start up just to have the computer set up the way I want it. I really thought that there would be a way to have the configuration take care of everything.

Thanks for the reply. I am sorry if I sound ungrateful, I really am not.

---

### Post by Kraut~salat on 2009-05-11
i don't think you need to do that in xorg.conf.
You can just use the gnome tool for that: System/Preferences/Display

It should save your setting between boot-up, works for me.

---

### Post by zcrar70 on 2009-06-26
I have exactly the same problem - either I can make the second screen appear in the correct position (to the right of the main screen), or it can be rotated, but not both at once.

If the screen is in the correct position, it will still be in landscape mode.

If the screen is rotated, it will mirror the main display.

I also worked around this by using xrandr in my .xsession, but this doesn't seem right, and causes the screen to flicker as I log on (as resolutions are changed etc.)

---

