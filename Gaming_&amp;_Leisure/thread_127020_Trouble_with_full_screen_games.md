---
title: "Trouble with full screen games"
date: 2006-02-07
forum: Gaming &amp; Leisure
---

### Post by Piggah on 2006-02-07
Hi,

I've been trying to play some full screen games lately, specifically Super Tux and Planetpenguin Racer, and whenever I try to go full screen, the screen usually slides over leaving half of the screen black and my cursor moves incredibly slow. I also get an error on my monitor about my input signal being out of range. I'm not sure why it's doing this, so any help is really appreciated. I don't know if this is a hardware issue, or something else. I only have graphics problems with these, so I'm kinda stumped. I think it could possibly be a game problem, but I don't know much.  

Oh, and I have ATI Radeon X800GT. 

Thanks in advance. :)

---

### Post by ZylGadis on 2006-02-08
Do you by any chance have two monitors?
I have exactly the same problem on a two-headed machine. The resolution is 2560x1024. Some full-screen games like the ones you mentioned seem to use the right monitor for primary, thus leaving the left one black and half of their display out of my visual field.
I have not yet gotten to solve that, but the solution seems quite easy - fiddle with the drivers a bit to tell the game which the primary monitor is, or disable one of them when going full-screen.
I have a GeForce FX5200, by the way.

---

### Post by Piggah on 2006-02-08
Nope, I only have one monitor. =\

edit: forgot to mention, i do have the fglrx ati drivers installed.

---

### Post by siorai on 2006-02-11
[QUOTE=Alex.P]Do you by any chance have two monitors?
I have exactly the same problem on a two-headed machine. The resolution is 2560x1024. Some full-screen games like the ones you mentioned seem to use the right monitor for primary, thus leaving the left one black and half of their display out of my visual field.
I have not yet gotten to solve that, but the solution seems quite easy - fiddle with the drivers a bit to tell the game which the primary monitor is, or disable one of them when going full-screen.
I have a GeForce FX5200, by the way.[/QUOTE]

I think that you need to specify your MetaModes in the Screen section of your xorg.conf. Mine looks like this:

```
Option         "MetaModes" "1280x1024, 1680x1050; 1280x1024, 1280x1024; 1280x1024, 1152x864; 1024x768, 1024x768; NULL,1680x1050; NULL,1280x1024; NULL,1152x864; NULL,1024x768"
```

By having the NULL entries, it will disable the secondary when a game wants to go fullscreen. My secondary is to the left of my primary.

---

### Post by Dianoga on 2006-03-14
I am having this same problem. I tried the metamodes and it didn't work for me.

Any advice on this one?

Also an ATI x800 GT with fglrx drivers.

---

### Post by nan0meter on 2007-07-16
You can try backing up your existing xorg.conf file (copy not move!) and do fglrxconfig again and ensure you're using the latest drivers.

If that doesn't work you can try to download the newest ati drivers from their site or look at there forums to see if someone opened a bug.

---

### Post by acoustibop on 2007-07-16
> **Piggah said:**
> ... I also get an error on my monitor about my input signal being out of range... 

Is it possible the game is trying to use a resolution or refresh rate your monitor can't handle, Piggah?

---

