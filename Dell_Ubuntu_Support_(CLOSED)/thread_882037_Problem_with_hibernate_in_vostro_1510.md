---
title: "Problem with hibernate in vostro 1510"
date: 2008-08-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by james86 on 2008-08-06
I can't have a successful hibernate with this laptop in Ubuntu 8.04 64 bits.

When is hibernating appears this problem on screen:

[24869.440636] uvcvideo:Failed to query (1) UVC control 2 (unit 0): -71 (exp. 26).
[24869.440641] uvcvideo 6-3:1.1: resume error -5

Any idea? thanks!

---

### Post by funkydan2 on 2008-08-08
I'm not sure how different the 1510 is from the 1500, but [this post]("http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/") has made suspend work a bit better on my Vostro 1500.

---

### Post by james86 on 2008-08-11
Vostro 1510 is the new version of model vostro. I am not sure that page works for me because explain a problem with a nVidia card, and I just have the integrate intel graphic card: Media Accelerator X3100.

I think this is a problem to considerate because there is gonna be a lot of people with this model and this grapich card in a short time.

---

### Post by dfrandin on 2008-08-12
This also occurs on my Vostro 1400.. I've determined those errors appear to be from the built-in webcam. I've not spent much time investigating why hibernate doesnt work on my 1400 as the cold startup/shutdown is fast enough for me, and I don't really need hibernation, but it would be nice to fix the one remaining "nit" with Ubuntu on my Vostro 1400.... I'll be standing by on this thread to see if anybody else is seeing this and what the fix is...

Dave

---

### Post by pelle.k on 2008-08-12
Try creating **/etc/pm/config.d/config** and put this in that file;
```
SUSPEND_MODULES="uvcvideo"
```

---

### Post by lvshankar on 2009-02-18
My suspend is proper, but on waking up its groggy[:D]
each time, something different happens. i've listed those different things:

1) youtube vids play at high speed (w/o sound)
2) rhythmbox or totem doesn't work, even with play pressed, nothing plays; no sound, no progress in progress bar. (it was open and playing before sleep)
3) firefox's top bar ain't visible and gnome's system trays (both up and down) are invisible, unless i do a alt+space then minimize it. other windows in maximized mode are proper
4) sometimes 1 and 2 occur together

attaching my dmesg log (tarred)

Ubuntu Intrepid Ibex (32)
Vostro 1510 w/ Intel Media Accelerator X3100

---

### Post by pelle.k on 2009-02-18
Necromancing are we? :)
Put this in **/etc/pm/sleep.d/01alsareload**
```
#!/bin/bash

case $1 in
    thaw|resume)
        alsa force-reload
        ;;
    *)  echo "nothing to do."
        ;;
esac
```
Make it executable ```
sudo chmod +x /etc/pm/sleep.d/01alsareload
```

That may take care of brute-force restarting alsa _after resuming_. It's going to shut down the volume applet and what not that is using alsa ATM.
If that's not enough, try ```
/etc/init.d/alsa-utils restart
```

And as a last resort, try shutting pulseaudio off
```
pulseaudio -k
```

You may want to try changing all devices under **System>Preferences>Sound** to ALSA instead of autodetect as well. These are som of the tricks i've learnt over the years.

Regarding graphics, you may want to disable "Desktop Effects" (aka compiz fusion).

---

### Post by lvshankar on 2009-02-20
> **lvshankar said:**
> 
3) firefox's top bar ain't visible and gnome's system trays (both up and down) are invisible, unless i do a alt+space then minimize it. other windows in maximized mode are proper


ok, now that part is permanent now. even after multiple normal shutdowns...

---

### Post by lvshankar on 2009-02-20
OK, that's fixed now.

I started firefox in safe mode and 'reset all toolbars..' etc and restarted

but, on waking up, the same happens.

---

