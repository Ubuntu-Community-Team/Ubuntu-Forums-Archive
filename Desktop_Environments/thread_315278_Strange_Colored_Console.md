---
title: "Strange Colored Console"
date: 2006-12-08
forum: Desktop Environments
---

### Post by KucingKelabu on 2006-12-08
Hello guys,

I'm using Edgy 32bit on my nVidia 6150 (in-built) + Samsung Syncmaster 205BW (20" Wide LCD, 1650x1080). I have this irritating problem:

Every time I switched to the console (ctrl_alt_f1, etc) after the Xserver loads, my screen will be splotched like below (i said like because these are the shutting down screen, which also have similar effect):

[[IMG]http://img98.imageshack.us/img98/903/02122006113we7.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=02122006113we7.jpg) [[IMG]http://img329.imageshack.us/img329/1077/02122006115ez3.th.jpg[/IMG]](http://img329.imageshack.us/my.php?image=02122006115ez3.jpg) [[IMG]http://img329.imageshack.us/img329/7774/09122006164hl3.th.jpg[/IMG]](http://img329.imageshack.us/my.php?image=09122006164hl3.jpg) [[IMG]http://img81.imageshack.us/img81/1447/25112006079np4.th.jpg[/IMG]](http://img81.imageshack.us/my.php?image=25112006079np4.jpg) 

It is irritating in sense that the fonts are hard to read, not to mention the colors. ](*,) 

However, the boot splash appeared correctly. Only the console/shutdown (basically after the xserver is loaded).

Killing the xserver while in console mode doesn't do anything.

Anyone have any idea on any workaround? (I've tried using vesa, nv, and finally nvidia drivers, but all yields the same)

Just in case, here's my Xorg.conf monitor section (i dont think it'll help, because even a freshly installed edgy pose this issue on my pc):

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection
```

:???:

---

### Post by K.Mandla on 2006-12-09
That's funny stuff. Any chance your hardware or connections are failing? I've seen similar behavior in a CRT that was on the verge of a nervous breakdown, and like yours, it only did that at certain resolutions. I'd swap the monitor as a troubleshooting measure, then try an add-on video card to see if the onboard video is misbehaving.

Good luck.

---

### Post by KucingKelabu on 2006-12-10
I did tests as you said - I tried my monitor on another comp (using Intel Gfx, also running ubuntu), and then I tried using 7300GT and 7600GS.

The monitor, console, colors, etc all work well with the intel card. So I think the monitor's fine :) Phew

Now here's an interesting thing. The artifact disappears with 7300GT, but appeared again when using 7600GS. Then I'm trying to look for the common feature of my 6150 and the 7600GS - Found it, TV Out!

And this is really is the culprit. A few searches in Google founds that if you disable the TV-Out, everything will be fine. So I tried it:

```
Section "Device"
    Identifier     "nVidia6150"
    Driver         "nvidia"

    Option "IgnoreDisplayDevices" "TV"
EndSection
```

Restarted the PC and logged into X. Switched to console, and Voila! My artifacts are gone for good.

On a side note, the TV-out will not be usable. Not a big deal for me though, as I don't use it at all.

---

