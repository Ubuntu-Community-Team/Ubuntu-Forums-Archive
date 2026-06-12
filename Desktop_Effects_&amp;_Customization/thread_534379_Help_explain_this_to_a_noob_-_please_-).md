---
title: "Help explain this to a noob - please :-)"
date: 2007-08-25
forum: Desktop Effects &amp; Customization
---

### Post by Nordkraft on 2007-08-25
Hi!

I've just installed Feisty on my laptop (an hp dv6507eo) with a GF7150M gfx-card. Now, I'd really like some of the cool desktop effects and themes I've seen on some screenshots. However, I'm not really sure what to install. Yes, I've read several how-tos on installing Beryl, CompizFusion and Emerald. My problem is of a more general nature though. 

Could someone please explain to me exactly what I need to install, and in what order, to have the compositing effects as well as being able to choose some of the ready-made themes. 

btw, I've installed the newest nvidia-drivers from nvidia's site using this how-to:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html) 

Cheers!

---

### Post by Patrick793 on 2007-08-25
> **Nordkraft said:**
> Hi!

I've just installed Feisty on my laptop (an hp dv6507eo) with a GF7150M gfx-card. Now, I'd really like some of the cool desktop effects and themes I've seen on some screenshots. However, I'm not really sure what to install. Yes, I've read several how-tos on installing Beryl, CompizFusion and Emerald. My problem is of a more general nature though. 

Could someone please explain to me exactly what I need to install, and in what order, to have the compositing effects as well as being able to choose some of the ready-made themes. 

btw, I've installed the newest nvidia-drivers from nvidia's site using this how-to:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html) 

Cheers!


For the basics, go to System, Preferences, Desktop Effects, then click enable.

---

### Post by Nordkraft on 2007-08-25
Cheers for the answer!

Two things though: 

1. clicking on "Enable Desktop Effects" gives me a message stating something along the lines of compositing is not enabled. Do I need to set "compositing" to "enable" in xorg.conf for this to work?

2. when the desktop effects are (eventually) enabled, will I be able to use the themes with transparency of windows, shadows etc.? And moreover, where do I get such themes - do I need to install Emerald?

Sorry to be so noobish :)

---

### Post by Rupertronco on 2007-08-25
Enabling the base desktop effects only has 2 plugins. The cube, and wobbly windows. However, if you can get these to work it's going to be indicative of whether you're able to install compiz-fusion right away, or if you need to get your 3-d acceleration working before you can move on to installation. You do need to enable compositing in order to get this to work. However if you're not familiar with manually setting up your xorg.conf file i'd suggest you first check by making sure your restricted drivers are active. You can do that by going to system>administration>restricted drivers manager.

---

### Post by ArtF10 on 2007-08-25
By enable compositing, do you mean changing xorg.conf's Composite from Disable to Enable?  Or is there more to it?

The reason I ask is because I got the same message as the user above, something about composite not enabled, and ALL I did after installing compiz fusion was to change xorg to Enable and reboot.  I then manually entered compiz --replace in Alt+F2 and so far its working...CUBE, wobbly, blah, blah blah.  And I never touched Desktop Effects at all, infact I removed it before installing Compiz Fusion.

This was ALL done in Gnome.

---

### Post by Rupertronco on 2007-08-25
> **ArtF10 said:**
> By enable compositing, do you mean changing xorg.conf's Composite from Disable to Enable?  

Yep, that's what I was referring to. The easiest way for someone who's new to the Ubuntu platform to tell if it's working is by enabling the default desktop effects (which are compiz by the way, just a version with many fewer plugins). 

I would not recommend manually editing your xorg.conf file unless you are comfortable doing so.

---

### Post by ArtF10 on 2007-08-25
> **Rupertronco said:**
> ...I would not recommend manually editing your xorg.conf file unless you are comfortable doing so.

Yeah, agreed with that.

---

### Post by Nordkraft on 2007-08-26
Thank you for the answers and suggestions :)
For some reason the restricted-drivers implemented in Ubuntu do not work for my gfx-card (GF7150M), so I had to install the ones from NVidia's site, but I'm hoping that they will work as well with the Desktop Effects.
What about themes then. Would I need to install Emerald on top of the compiz-fusion in order to get access to all the ready-made themes?

Cheers!

---

