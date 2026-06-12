---
title: "Compiz problem..."
date: 2011-11-27
forum: Desktop Environments
---

### Post by Plasma_NZ on 2011-11-27
ok basically im another who hates unity..

so running gnome fallback session...

go to turn on compiz and no matter what settings i use i get this problem


[IMG]http://iforce.co.nz/i/asmg1pz5.u3q.png[/IMG]

Im using up-to-date drivers..

Ubuntu 11.10 64bit


anyhow help would be awesome...

have also tried options of --sm-disable --indirect-rendering - nothing seems to help... disables all plugins in compiz etc.. still the same problem...

---

### Post by bluexrider on 2011-11-27
Try resetting compiz to its defaults:
  sudo gconftool-2 --recursive-unset /apps/compiz 

sudo reboot --

---

### Post by Plasma_NZ on 2011-11-27
> **bluexrider said:**
> Try resetting compiz to its defaults:
  sudo gconftool-2 --recursive-unset /apps/compiz 

sudo reboot --

Tried that, hasnt helped.... at this rate im going to revert back to 11.04, that worked flawlessly along with 10.10, but having nothing but issues with 11.10

if i could get this fixed everything will be sweet

---

### Post by thetruckinglife on 2011-11-27
well i reverted back to 10.10 and Compiz Fusion works flawless.
after having so many screen freezes with 11.04 and 11.10 it was the thing to do.

---

### Post by bluexrider on 2011-11-27
Yeah, had similar issues. I removed compiz completely but it didn't feel right so I moved back to 11.04

---

### Post by Plasma_NZ on 2011-11-27
> **thetruckinglife said:**
> well i reverted back to 10.10 and Compiz Fusion works flawless.
after having so many screen freezes with 11.04 and 11.10 it was the thing to do.

well i dont really want to revert back personally... 11.10 works fine for everything else except this compiz issue... once i have this resolved i'll be a happy camper....

---

### Post by thetruckinglife on 2011-11-28
> **Plasma_NZ said:**
> well i dont really want to revert back personally... 11.10 works fine for everything else except this compiz issue... once i have this resolved i'll be a happy camper....

yeah 11.10 works fine if you leave it alone ;)
i just like how easily 10.10 can be customized as i am one that will have a different theme every week.
besides its easier on the hardware in my older desktop that was designed for MS XP.

---

### Post by typhoon_tip on 2011-11-28
> **Plasma_NZ said:**
> well i dont really want to revert back personally... 11.10 works fine for everything else except this compiz issue... once i have this resolved i'll be a happy camper....

What video card and what video driver are you using ? Open Source driver or Proprietary driver ?

---

### Post by Plasma_NZ on 2011-11-28
> **typhoon_tip said:**
> What video card and what video driver are you using ? Open Source driver or Proprietary driver ?

i've tried, current and post and proprietary - all with the same results...

Video card is a Nvidia GTS 250 - the card is in mint condition as is the rest of my hardware....

---

### Post by vangop on 2011-11-28
I'd check ~/.xsession-errors, or /var/log/Xorg*log , dmesg?
Anything unusual there?
I've installed compiz on top of xubuntu 11.10, as well as on bare X. Works great.

---

### Post by Plasma_NZ on 2011-11-28
ok fresh install, using the gfx drivers from the install, have compiz setup nicely, albeit it seems the compiz plugins are the older ones, e.g there are no options tab in expo, or in place windows...

am about to install the "recommended addtional drivers" from ubuntu.... will report if that causes a issue..

---

### Post by Plasma_NZ on 2011-11-28
> **Plasma_NZ said:**
> ok fresh install, using the gfx drivers from the install, have compiz setup nicely, albeit it seems the compiz plugins are the older ones, e.g there are no options tab in expo, or in place windows...

am about to install the "recommended addtional drivers" from ubuntu.... will report if that causes a issue..

So far so good, no issues... apart from compiz using the old plugins, which is a real pain as i cannot use place-windows like i did previously..

If i can fixed expo and place-windows plugins - i'm all sorted..

---

### Post by Plasma_NZ on 2011-11-28
For some reason i have no idea how its happened...

but this is the place windows plugin - its completely different to previous install, missing alot of options....

[IMG]http://iforce.co.nz/i/e2tewbjt.nf2.png[/IMG]

And this here is the epxo plugin - once again missing lots of options...

both these plugins should have tabs up the top with different setting options....

[IMG]http://iforce.co.nz/i/3ts5bdog.qnx.png[/IMG]


Any ideas how i can updates these plugins without breaking compiz..?

---

### Post by typhoon_tip on 2011-11-28
> **Plasma_NZ said:**
> For some reason i have no idea how its happened...

but this is the place windows plugin - its completely different to previous install, missing alot of options....

[IMG]http://iforce.co.nz/i/e2tewbjt.nf2.png[/IMG]

And this here is the epxo plugin - once again missing lots of options...

both these plugins should have tabs up the top with different setting options....

[IMG]http://iforce.co.nz/i/3ts5bdog.qnx.png[/IMG]


Any ideas how i can updates these plugins without breaking compiz..?

I'm lost... How can it be a fresh install with that bar on the left ? Have you already tweaked it before starting checking compiz ? Are you using Unity or fallback session ?

---

### Post by Plasma_NZ on 2011-11-28
> **typhoon_tip said:**
> I'm lost... How can it be a fresh install with that bar on the left ? Have you already tweaked it before starting checking compiz ? Are you using Unity or fallback session ?


Fresh install, in a gnome-fallback-session - have installed avant, but from the very word go, the compiz plugins seemed to differ from last installed, irony is i've used the same method as last time...

im a little confused myself why the plugins seem to be different this time round..

---

### Post by Plasma_NZ on 2011-11-28
Ok...

I have found what causes the problem that i originally posted...

Basically when u install gnome-tweak-tool  - then in the option of

Desktop - "Have file manager handle desktop" - if i turn it off, i get that horrible clipping...

how can i turn it off and not get the clipping...?

---

### Post by thetruckinglife on 2011-11-28
> **vangop said:**
> I'd check ~/.xsession-errors, or /var/log/Xorg*log , dmesg?
Anything unusual there?
I've installed compiz on top of xubuntu 11.10, as well as on bare X. Works great.

i still suggest Maverick 10.10 :KS
i am really getting this Compiz fusion tweeked now learning how to set all the extra effects is cool.
i almost went and installed Windows 8 Developer Preview.
hope you get things worked out tho,i know your frustrations.

---

### Post by Plasma_NZ on 2011-11-28
Well my setup is now up to date and complete, everything runs flawlessly - just cannot remove the file-manager bar up the top until someone can tell me how to stop the clipping when i disable that bar.... apart from that... 11.10 is pretty good when u use gnome-shell and not unity...

---

### Post by Plasma_NZ on 2011-12-02
Not sure what happened.. fresh reinstall fixed the problem...

as for the clipping error, there seems to be a bug between ubuntu/compiz/gnome-tweak-tool 

in gnome-tweak-tool - then u select 

Desktop > file manager handle desktop > off  

causes the clipping problem... bug has been filed with launchpad and gnome-tweak-tool...

marking thread as solved...

---

