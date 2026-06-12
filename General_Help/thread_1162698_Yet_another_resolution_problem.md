---
title: "Yet another resolution problem"
date: 2009-05-18
forum: General Help
---

### Post by davexunit on 2009-05-18
I haven't yet been able to find the total solution to my problem from other threads as far I know.

Here's my story:
I'm using 9.04.
My monitor supports a max res of 1280x1024. i have this res in windows.
Ubuntu is only letting me set 1152x864 max res.
I figured out how to use xrandr to get 1280x1024:
```
xrandr --newmode 1280x1024 108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
xrandr --addmode DVI-0 1280x1024
xrandr --output DVI-0 --mode 1280x1024
```However, this setting is not remembered and goes away after i log out leaving me with 1152x864 max res again.
I tried adding some lines to xorg.conf with no luck.
I cannot figure out how to make ubuntu remember this setting so that i do not have to run a script manually every time to get the res that I want.

Any help is gladly appreciated.
Thanks.

---

### Post by CatKiller on 2009-05-18
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by Legace on 2009-05-18
1) Open xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

2) Add ModeLine to Monitor section (don't delete other values inside the monitor section):

```
    Modeline  1280x1024 108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
```

3) Add subsection Display->Modes into "Screen" section.
```
	SubSection "Display"
	Modes      "1280x1024"
	EndSubSection
```

End result should look something like this. The example below is purely an example. Do not use the values below. Only use the values above.
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
    Modeline  "1280x1024" 110.00 1280 1328 1512 1712 1024 1025 1028 1054
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
	Modes      "1280x1024"
	EndSubSection
EndSection
```

---

### Post by davexunit on 2009-05-18
Using the tips from both of you and using the specs of my monitor, I know have an xorg.conf that looks like this:
```
Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync       30-70
    VertRefresh     50-160
    Modeline        "1280x1024" 108.88  1280 1360 1496 1712  1024 1025 1028 1060 -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"        
        Virtual    1280 1024
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "False"
EndSection
```However, i still cannot select 1280x1204 from the display dialog.
I'm a bit stumped on this one.
Is there anything else I could possibly do?

---

### Post by CatKiller on 2009-05-18
> **davexunit said:**
> Is there anything else I could possibly do?

You could try them independently; comment out the modeline (put a # at the start of the line) and see if works and, if it doesn't, uncomment the modeline and comment out the refresh rates and see if it works.

** /var/log/Xorg.0.log** should tell you why a particular mode is being rejected.

Sometimes, rather than not giving any EDID values, a monitor will give erroneous ones. Mine does this. One solution is to tell X to ignore any values that it's been given and to just use the ones in xorg.conf by putting ```
        Option          "UseEDID"                       "False"
``` in the "Device" Section.

If you want even more information about why the modes are rejected in the log, you can add ```
        Option          "ModeDebug"                       "True"
``` to the "Device" Section.

---

### Post by davexunit on 2009-05-18
I tried adding those lines to xorg to no avail with various combinations of lines commented out.
The log mentions nothing about rejecting the video mode. In fact it doesn't mention that resolution at all.
Um, anything else that I should try?

---

### Post by Legace on 2009-05-18
Do you have an ATi graphics card? If you do, are you using the FGLRX driver? Because FGLRX ignoes modelines.. :/

---

### Post by davexunit on 2009-05-18
I have an ATI Radeon x1950 Pro. And the fglrx drivers i downloaded only crash x, i had to remove them from the command line and go back to the open-source radeon driver. But that's another story for another day.
So to make a short story long, I'm using the radeon drivers, not fglrx.

---

### Post by Legace on 2009-05-18
> **davexunit said:**
> I have an ATI Radeon x1950 Pro. And the fglrx drivers i downloaded only crash x, i had to remove them from the command line and go back to the open-source radeon driver. But that's another story for another day.
So to make a short story long, I'm using the radeon drivers, not fglrx.

Comment out the following:
    HorizSync       30-70
    VertRefresh     50-160

And add the following under the modeline..
```
Option "PreferredMode" "1280x1024"
```

---

### Post by davexunit on 2009-05-18
Still nothing. Grr. :[

---

### Post by Legace on 2009-05-18
Type in following and post output:
```
glxinfo |grep vendor
```

---

### Post by davexunit on 2009-05-18
```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

```

---

### Post by Legace on 2009-05-18
Can't help any further.. Someone else maybe knows better..

Sorry :/

EDIT: Try to add that the following to ~/.xprofile
Then it will be automatically executed (I think)..

```
xrandr --newmode 1280x1024 108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
xrandr --addmode DVI-0 1280x1024
xrandr --output DVI-0 --mode 1280x1024
```

---

### Post by davexunit on 2009-05-18
Thanks for trying!

---

### Post by Legace on 2009-05-18
Try to add that the following to ~/.xprofile
Then it will be automatically executed (I think)..

```
xrandr --newmode 1280x1024 108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
xrandr --addmode DVI-0 1280x1024
xrandr --output DVI-0 --mode 1280x1024
```

---

### Post by davexunit on 2009-05-18
The only problem with that is that it won't execute immediately at the start of x but rather when i log on. and it will only affect my user, not others.
It seems a good temp fix though until a better solution comes around.
Thanks!

---

### Post by Legace on 2009-05-18
This will apply to GDM (and all uses).

Note, remove the xprofile first.

Try to add that the following to /etc/gdm/PreSession/Default
(to the end of the file)

```
xrandr --newmode 1280x1024 108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
xrandr --addmode DVI-0 1280x1024
xrandr --output DVI-0 --mode 1280x1024
```

---

### Post by davexunit on 2009-05-18
I'm guessing I should put it before exit 0?

---

### Post by Legace on 2009-05-18
> **davexunit said:**
> I'm guessing I should put it before exit 0?

Yeah :)

---

### Post by davexunit on 2009-05-18
Alright that worked! Thanks a lot! I always have problems getting to this resolution even in Windows. Although I must admit it was very easy to force a resolution in Windows.

---

### Post by Legace on 2009-05-18
> **davexunit said:**
> Alright that worked! Thanks a lot! I always have problems getting to this resolution even in Windows. Although I must admit it was very easy to force a resolution in Windows.

Glad it worked out finally :) Enjoy..

---

### Post by davexunit on 2009-05-18
I think the display preferences dialog should have an option like Windows to choose an un-supported resolution for people with dumb monitors like mine. It sure would save people a lot of trouble.

---

