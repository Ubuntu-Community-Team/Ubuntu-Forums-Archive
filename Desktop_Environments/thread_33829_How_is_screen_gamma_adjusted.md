---
title: "How is screen gamma adjusted?"
date: 2005-05-12
forum: Desktop Environments
---

### Post by ramtap on 2005-05-12
I feel slightly foolish asking this, I'm sure the answer is obvious but even so I've been scratching my head for an hour now. 

How are the display preferences altered in Hoary Hedgehog? and particularly, how is the screen gamma adjusted? I use an Intel i810 which has a chokingly dark default setting and until I can alter it Ubuntu is lurking in shadows. 

Thanks!

---

### Post by shakin on 2005-05-12
My i915 works ok, but I have this problem with a very old ATI Rage II card that uses the vesa driver (can somebody recommend a better driver?)

If you use KDE there is a gamma setting in the control panel. For whatever reason that doesn't work on my ATI card, maybe due to insufficient driver support with vesa. The only other way I know how to do it is by adding a Gamma line in the monitor section of /etc/X11/xorg.conf:

```

Gamma 2 2 2

```

2 2 2 correspond to the RGB channels so you can tweak the color output as well. This also doesn't work with my ATI card. It sucks. Hopefully you have better luck than I did.

---

### Post by ramtap on 2005-05-12
Thanks for that Shakin. I'm using Gnome which doesn't have the same control panel. My old gamma setting was 1.79 under windows, would this translate to "gamma 1.79 1.79 1.79"  in the conf file? 

Also is there a similar setting for the overlay gamma?

---

### Post by shakin on 2005-05-12
[QUOTE=ramtap]Thanks for that Shakin. I'm using Gnome which doesn't have the same control panel. My old gamma setting was 1.79 under windows, would this translate to "gamma 1.79 1.79 1.79"  in the conf file?[/QUOTE]

That's a good place to start, but due to differences in the driver I'm sure it won't be an exact match.

[QUOTE=ramtap]Also is there a similar setting for the overlay gamma?[/QUOTE]

I have no idea. I don't even know what overlay gamma is :)

You might also want to try running 'xgamma'. You might be able to change during runtime with that, which would simplify the process.

---

### Post by ramtap on 2005-05-12
The overlay is for video rendering - it's on a separate layer on the graphics card and on my card at least it isn't affected by the display gamma setting. Unluckily my system isn't powerful enough to render video smoothly without without the overlay so I'm keen to find a fix for this. 

Thanks again for the advice.

---

