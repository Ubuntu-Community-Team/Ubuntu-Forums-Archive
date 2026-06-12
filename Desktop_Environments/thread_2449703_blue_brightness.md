---
title: "blue brightness"
date: 2020-09-01
forum: Desktop Environments
---

### Post by francisaccount on 2020-09-01
Hello!

I'm new to Lubuntu, I was using ubuntu 18 before. Since I installed Lubuntu, my screen looks blue. Only when the brightness of the screen is at its maximum, the screen looks white. But when I turn down the brightness, it does not turn progressively to black, it turns to a dark blue color. In between, it really looks blue (a white color shows up like very light blue).

How can I change the brightness system such that my screen doesn't look blue?

I tried to use Redshift. It is at 6500K right now, but the screen still looks rather blue.

Thank you for your help!

---

### Post by guiverc on 2020-09-01
I can't give any meaningful help (*I setup my redshift back in 16.04 days and haven't adjusted it since*).

From the 6500 setting I gather you're talking *temperature*. It has many other settings, and in my case I just played until I achieved what I wanted.

I use the same setting on Lubuntu *groovy* I'm now running, as with any other desktop (*if using GNOME I disabled Night Light so it doesn't interfere with my redshift setup*), so I believe it's not Lubuntu specific  (*I also have multiple desktops installed on this system, and I use the same settings on each*).

I'll refer you to [https://help.ubuntu.com/community/Redshift](https://help.ubuntu.com/community/Redshift)

and I suggest you look at the GAMMA settings. You can set values for  both day & night.

I'll also provide a link to [https://docs.redshift3d.com/display/RSDOCS/Gamma](https://docs.redshift3d.com/display/RSDOCS/Gamma)  though I doubt you'll need it.

---

### Post by ajgreeny on 2020-09-01
Find the configuration file used by red shift, normally in your home .config folder.
In there you will find the colour temperature settings in use.

Reduce the 6500 down to about 5500 as a test and see what difference it makes; I use 6500 for daytime and 4000 for nightime, but try out as many as you like to until you display temp suits you.

In previous versions of Ubuntu it was necessary to add redshift to the geoclue configuration as well or the autochanges did not work, if that was how your timing was set up; I'm  on an Android tablet at present so can not look for the added text in geoclue.conf but will find it later and add it to this thread. If you use manual location all this may not matter to you.

---

### Post by ajgreeny on 2020-09-02
The edit you need to make for geoclue to work properly is to add the following section at the bottom of ***/etc/geoclue/geoclue.conf***

You will see many other similar application entries in this file, probably including firefox, with the same stanza but just the application name changed.
```
[redshift]
allowed=true
system=false
users=
```
Without this entry redshift will not be able to use geoclue and you will have to set location manually, OK if you never travel around much, but annoying if you move east or west across the globe for work or vacations.

---

### Post by francisaccount on 2020-09-05
Thank you very much for your help!

I now have a red brightness. That's much butter for my eyes I think. So redshift does its job. If I have more time, I will look further why I has been a blue brightness and look specifically to the gamma color.

Thanks a lot!

---

### Post by ajgreeny on 2020-09-05
Have look at the output of command ```
xrandr --verbose | grep -i gamma
``` which will show the current gamma levels for red, green and blue in that order.

Maybe your redshift.conf file has the levels set strangely; I have mine set as 1.0 for all three colours and just change the colour temperature.

---

