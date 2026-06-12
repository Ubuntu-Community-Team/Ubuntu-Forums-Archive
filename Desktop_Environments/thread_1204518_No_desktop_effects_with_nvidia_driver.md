---
title: "No desktop effects with nvidia driver"
date: 2009-07-04
forum: Desktop Environments
---

### Post by triangleSLO on 2009-07-04
I installed nvidia 180 driver via System/Administration/Hardware Drivers but there is no way i can enable effects. Does anyone have a solution?

---

### Post by starcraft.man on 2009-07-04
What do you mean by no way to enable desktop effects? Are you saying you don't know how to turn on effects? Or that you have and it wouldn't work?

To enable desktop effects go to System > Preferences > Appearances > Visual Effects > Click normal.

The only problem you could have is if the driver isn't properly installed. To verify just look in the hardware drivers menu you used and it should be enabled.

Also, what make and model on the card?

---

### Post by merlinus on 2009-07-04
I am having the same problem of not being able to activate desktop effects.  According to System/Administration/Hardware Drivers, the nvidia 180 driver is activated and currently in use.

I have a geforce 9400 gt with 512MB VRAM.

---

### Post by triangleSLO on 2009-07-04
I know how to enable effects but when I try it searches for drivers and then it says it is not possible to enable effects.
I checked in menu and card is enabled.
I have geforce 6600.

---

### Post by drs305 on 2009-07-04
If either of you is trying to turn on the Desktop Effects via the Appearance tab, the screen blinks several times, and ends up stating something about "Unable to enable Desktop Effects", AND your hardware driver supports Compiz, see if Metacity's compositing is turned on. Turn it OFF to start Desktop Effects:
```

gconftool-2 -s -t bool /apps/metacity/general/compositing_manager false

```
Then select "Normal" or "Extra".

If it still doesn't work, you might want to run "compiz-check", a small script that tells you if you are missing something necessary to run compiz. Get the script here:
[compiz-check]("http://forlong.blogage.de/entries/2008/4/28/Introducing-Compiz-Check--a-script-to-test-and-troubleshoot-your-Compiz-install")

---

### Post by triangleSLO on 2009-07-04
This looks bad 

```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV43 [GeForce 6600] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

---

### Post by merlinus on 2009-07-05
FWIW, I got the same results.  Hard to believe that a geforce 9400 gt with 512MB VRAM cannot run compiz!  Something clearly is amiss...

---

### Post by Mayfairy on 2009-07-05
> **merlinus said:**
> FWIW, I got the same results.  Hard to believe that a geforce 9400 gt with 512MB VRAM cannot run compiz!  Something clearly is amiss...

Indeed, but not on the video card side. 
Both of those cards should be capable of running CompizI had the 6600 and no problems with it. 

Don't know if this helps any, but you could try reinstalling compiz. It *might* be the culprit if you've recently updates to Jaunty.

---

### Post by merlinus on 2009-07-05
Removed compiz and compiz-gnome, then reinstalled, via synaptic.  Still no go.

---

### Post by triangleSLO on 2009-07-05
This check is from my 3 years old dell laptop, but it can run compiz. This is weird.
 ```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

---

### Post by drs305 on 2009-07-05
> **triangleSLO said:**
> This check is from my 3 years old dell laptop, but it can run compiz. This is weird.


For merlinus, I agree with mayfairy, it's not your card's capabilities that are the issue. For triangleSLO, I don't know about the 6600 card (7600 works fine for me).

This thread deals mostly with later cards, which should help merlinus. TriangleSLO may be able to use the thread and learn something from tinivole's advice on reinstalling things. 
[http://ubuntuforums.org/showthread.php?t=1125400&highlight=180]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=180")

---

### Post by merlinus on 2009-07-05
Thanks for the thread link.  Unfortunately, perhaps because I did not follow the directions closely enough, it did not work for me.

However, after being stuck in low resolution because of a failure to properly activate the new kernel mode (or some such error), uninstalling the latest driver via the terminal commands and then going through a now familiar process of reinstalling the 180.44 driver and configuring via the nvidia settings gui, now I can activate both the normal and extra visual effects.

My only guess is that some recent upgrade had changed something, and the install, uninstall, and reinstall process fixed whatever that was.

Ain't computers fun!

---

