---
title: "Screen resolution automatically reset to native resolution after manual setting"
date: 2021-09-17
forum: Desktop Environments
---

### Post by fretros on 2021-09-17
I have exactly the same resolution issue as this thread [https://ubuntuforums.org/showthread.php?t=2413978](https://ubuntuforums.org/showthread.php?t=2413978)  (but w/o the audio part) but since it's closed I couldn't use the existing thread.

We're using a lot of Intel NUCs running Xubuntu 18.04 (from a cloned image), all with different displays, some Full HD, some 4K. But they all support 1920x1080, which is the resolution we need to display content in a browser.
But when a NUC with a 4K display display is set to 1920x1080 using xrandr, it briefly works in that resolution (and the display's OSD shows the new smaller resolution), but somehow something in Xubuntu resets the resolution to the native 4K, which isn't what we want. 

Is there any way to override this behaviour? I want to be able to force the resolution to something less optimal. I *do* know the display supports the smaller resolution (and it's listed in the xrandr output as welll)

---

### Post by &amp;KyT$0P# on 2021-09-18
Can you change it in Xfce settings instead?  If not can you somehow sync Xfce display settings, which are stored in xfconf, with what you're setting using xrandr?

---

### Post by fretros on 2021-09-20
Changing it in Xfce yields the same result. It briefly changes the resolution, but "something" changes it back to the display's preferred resolution immediately afterwards (I mean 1 or 2 seconds or so).

I'm not sure what you mean with the syncing Xfce with the xrandr command line. This is my xrandr command line:

xrandr --output HDMI-1 --mode 1920x1080 --rate 60 --rotate normal --reflect normal

(not setting rotate en reflect has the same effect, it's just part of the script)

---

### Post by &amp;KyT$0P# on 2021-09-22
Have you ruled out hardware issues, e.g. problem with the cable connecting to the display?

> **fretros said:**
> I'm not sure what you mean with the syncing Xfce with the xrandr command line.

I mean if you use xrandr to set display settings, make sure the Xfce display settings match what you have set with xrandr.  I've seen cases where Xfce display settings being out of sync with other methods of configuring display settings results in reverting to undesired display configuration.

---

### Post by fretros on 2021-09-23
OK, I see,
but the same happens in both cases, Xfce via gui and xrandr via cli.
It's clearly some process that resets the resolution back to the preferred resolution (4K), 2 seconds after I manually changed it to full hd.

BTW: the display *does* support full hd, it's not that I try to set it to some exotic resolution, full hd 1920 * 1080 60p is listed in the accepted resolutions in de xrandr output. 
I just need to find the process that does the reset of the resolution.

---

