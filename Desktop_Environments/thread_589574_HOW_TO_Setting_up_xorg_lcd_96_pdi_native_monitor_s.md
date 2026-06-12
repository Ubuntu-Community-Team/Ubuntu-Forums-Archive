---
title: "HOW TO: Setting up xorg lcd 96 pdi native monitor settings"
date: 2007-10-24
forum: Desktop Environments
---

### Post by TuxCrafter on 2007-10-24
HOW TO: Configure X to start with 100 dpi, and hereby solving many font rendering problems

#Version:       0.0.3
#Date:          06-11-07
#Description:   Setting up gdm to start with 100 dpi resolution monitor settings
#Solution:      This script will try to fix system width bad rendering of fonts

These script has both community support and commercial support.

Please post all your feedback about this script so I can continuously keep improving it.

I hope this script will help a lot of people!

-- -- -- -- --

This script will change your gdm settings and forces the xserver to start with 100 dpi, and by doing this resolving many font problems.
If you start the xserver with the startx command it should already start with 100 dpi

Please run the below commands, if your resolution is below 96 dpt and/or not symmetric. You can try this script to get your dpi resolution corrected.

```
xdpyinfo | grep resolution
    resolution:    100x100 dots per inch
xdpyinfo | grep dimension
    dimensions:    1024x768 pixels (260x195 millimeters)
```You can check your dpi xserver settings with the below command
```
ps aux | grep /usr/bin/X11/X
    root      3725  4.1  1.7  21648 17452 tty2     Ss+  11:25   1:34 /usr/bin/X11/X -dpi 100 -nolisten tcp
```(ps the views of the script will be auto reset to zero, so this is not a very well indicator of the scripts popularity)

---

### Post by K.Mandla on 2007-10-26
Moved to Desktop Environments.

---

### Post by TuxCrafter on 2007-10-26
version upgrade with higher calculation resolution

---

### Post by NoFearDJB on 2007-10-26
Do you have any before and after screenshots? I'm wondering if i need this or if this is just a fix for some people.

---

### Post by TuxCrafter on 2007-10-26
> **NoFearDJB said:**
> Do you have any before and after screenshots? I'm wondering if i need this or if this is just a fix for some people.

```
xdpyinfo | grep resolution
```

Please run the above command if the left and right difrence more than a few dots, and/or if your relolution is below 96 dpt. You can may try the script to get your dpi font resolution corrected.

An example of a correct resolution:
resolution:    95x96 dots per inch

---

### Post by NoFearDJB on 2007-10-30
```
$ xdpyinfo | grep resolution
  resolution:    98x98 dots per inch

```
I think I'm good :)

---

### Post by TuxCrafter on 2007-10-30
> **NoFearDJB said:**
> ```
$ xdpyinfo | grep resolution
  resolution:    98x98 dots per inch

```I think I'm good :)

Indeed your resolution is fine. If you got problems with your font it's in something else.

---

### Post by adlin5000 on 2007-11-04
[EDIT] Just found your other post. Sorry.


Finally something that sounds like a fix. I have been hunting for a fix for this for about 3 months now. I can get 96x96 in my xorg.conf, but xfce overrides this down to 45x45. I have to bump the font sizes up to 20 just to be readable, but this causes Firefox to have display issues. You said in your first post you had a script for xfce, if you could post it that would be great. Thanks

---

### Post by TuxCrafter on 2007-11-04
> **adlin5000 said:**
> [EDIT] Just found your other post. Sorry.


Finally something that sounds like a fix. I have been hunting for a fix for this for about 3 months now. I can get 96x96 in my xorg.conf, but xfce overrides this down to 45x45. I have to bump the font sizes up to 20 just to be readable, but this causes Firefox to have display issues. You said in your first post you had a script for xfce, if you could post it that would be great. Thanks

nice that it helped and thanks for voting  in the poll

---

### Post by hotweiss on 2007-11-04
This script did not help... I tried a number of different resolutions and I had no luck with this tiny font solution script. Any other ideas?

---

### Post by hotweiss on 2007-11-04
OK, after changing the resolution a few times my DPI is back to normal thanks to your script. WOW, this is a pretty serious bug in Xubuntu... THANKS

---

### Post by TuxCrafter on 2007-11-04
> **hotweiss said:**
> This script did not help... I tried a number of different resolutions and I had no luck with this tiny font solution script. Any other ideas?

how. .you cant use more then one resolution... there is only one resolution optimal for the LCD and you have to make sure you use the correct video driver and resolution mode. than you use this script for that resolution mode to setup the dpi settings.

---

### Post by hotweiss on 2007-11-04
> **TuxCrafter said:**
> how. .you cant use more then one resolution... there is only one resolution optimal for the LCD and you have to make sure you use the correct video driver and resolution mode. than you use this script for that resolution mode to setup the dpi settings.

I set it to 1024x768 as my notebook is that resolution and my external LCD is 1440x900, this way 1024x768 will work on both screens with out any problems. After I ran your script, I rebooted and nothing changed. So then I changed the type of LCD and set the resolution to 1024x768 and then Xubuntu set the resolution at 800x600, so I changed backed everything again to the original correct settings and my DPI was back to normal. I'm sure it's thanks to your script as that didn't work before without using your script.

---

### Post by adlin5000 on 2007-11-05
I DID IT!
Finally got it to work. It seems that XFCE used the EDID info from the monitor to determine the display size and then calculates the DPI from that. I had to edit the xorg.conf file to ignore EDID and DDC and put in all the monitor settings (H/V rates, display sixe, and resolutions). After that XFCE had to go from those settings because there was nothing else for it to use. Now I have 96x96 DPI, readable text and web sites look like they should.

I'll post this with the other script as this deals with both XFCE and Xorg.

Thanks for all your help.

---

### Post by TuxCrafter on 2007-11-06
Created a new script that solves the problem by starting X with a dpi resolution of 100, instead of setting the monitor display size. This should create a better and more system width solution for the problem.

---

