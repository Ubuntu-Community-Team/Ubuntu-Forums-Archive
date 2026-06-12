---
title: "Some trouble with setting up my dual screen"
date: 2011-03-07
forum: Desktop Environments
---

### Post by Joorik on 2011-03-07
Hey guys,

this is the frist time I've installed Ubuntu as my main OS, but I'm having some trouble.I cannot get my dual screen setup to work properly.

I'm running a gigabyte mobo, with an core i5 and a Nvidia 8800 GTS 320mb video card (2x dvi). My monitors are a 24 inch acer (1920x1200) and a 32 inch Phillips TV (1920x1080). 

The main screen, the acer, is working just fine with his max resolution via a DVI cable. My tv is connected via a DVI to HDMI converter and it does work, but only at 640x480 resolution. The screen is very small in the center of the TV.

I've tried changing the resolution in the xorg.conf file but upon restarting it just turned my TV off.

Anyone knows how I can fix this?

---

### Post by inobe on 2011-03-07
have you enabled the **"additional drivers"**?

example video [http://www.youtube.com/watch?v=MaPOMLaHOxA](http://www.youtube.com/watch?v=MaPOMLaHOxA)

activating the driver will take some time, not only does it activate and set it up, it needs to download the driver first, so be patient.

after done, you will be prompted to restart computer, once restarted, search for nvidia settings in your menu.

in nvidia settings you will be able to configure your monitors.

---

### Post by Joorik on 2011-03-07
> **inobe said:**
> have you enabled the **"additional drivers"**?

example video [http://www.youtube.com/watch?v=MaPOMLaHOxA](http://www.youtube.com/watch?v=MaPOMLaHOxA)

activating the driver will take some time, not only does it activate and set it up, it needs to download the driver first, so be patient.

after done, you will be prompted to restart computer, once restarted, search for nvidia settings in your menu.

in nvidia settings you will be able to configure your monitors.

Yup, done both of these things already, I also used the nvidia x server to configure it but it still doesn't work

---

### Post by inobe on 2011-03-07
i think it's the converter, they are not backwards compatible like many believe!

i have one as well, basically i bought it for nothing, it would have been useful hdmi> dvi, and not the other way around.

i tried with different operating systems, the results were different, but unsatisfying.

---

### Post by Joorik on 2011-03-07
> **inobe said:**
> i think it's the converter, they are not backwards compatible like many believe!

i have one as well, basically i bought it for nothing, it would have been useful hdmi> dvi, and not the other way around.

i tried with different operating systems, the results were different, but unsatisfying.

I'm currently posting this from the same PC running windows 7 with the screen on full HD resolution (IT does show up as a "Generic Non PnP Monitor"). 

Do you think it will work with the converter or should I stop using ubuntu already since I really want the dual screen to work :(

---

### Post by jwcalla on 2011-03-07
Do you have the correct HorizSync and VertRefresh frequencies for the TV in your /etc/X11/xorg.conf?

---

### Post by Joorik on 2011-03-07
> **jwcalla said:**
> Do you have the correct HorizSync and VertRefresh frequencies for the TV in your /etc/X11/xorg.conf?

Uhm, I guess not, where can I find those values? (Tv is a Philips 32PFL7605, 100 hz)

---

### Post by jwcalla on 2011-03-07
> **Joorik said:**
> Uhm, I guess not, where can I find those values? (Tv is a Philips 32PFL7605, 100 hz)

You could see if there is any information or driver files on the Philips website (I checked quickly but couldn't find anything... since it is a TV after all), or you can contact Philips for the right numbers.

Or you could load up Windows and search for the actual "Generic Non PnP Monitor" driver file and see what values they have in there.  I don't know where they store the driver file but I think it's typically a .INF file.

Since the TV isn't capable of sending these values to the video card automatically (probably because of the DVI / HDMI converter), they have to be specified with a driver file (Windows) or in the xorg.conf (linux).

---

### Post by inobe on 2011-03-08
> **Joorik said:**
> I'm currently posting this from the same PC running windows 7 with the screen on full HD resolution (IT does show up as a "Generic Non PnP Monitor"). 

Do you think it will work with the converter or should I stop using ubuntu already since I really want the dual screen to work :(

i solved my particular problem with composite cables.

my nvidia card came with a composite cable adapter.

---

