---
title: "tvtime XGL Issues"
date: 2006-06-07
forum: Desktop Environments
---

### Post by kg4gyt on 2006-06-07
Hello,
I have xgl working exactly how I like, however whenever I run tvtime I get the following error.
```

user@kg4gyt-linux:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/user/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

```

I'm using an nvidia card (FX 5700 Ultra)

Any help as to how to make it work again would be great.  Thanks

---

### Post by gala on 2006-06-08
Same problem here

---

### Post by traveller.ct on 2006-06-08
You need to enable Xv overlay in your graphics card.

I only know how to do this with an ATI card using the fglrx driver since that's what I have.

You can enable Xv overlay by directly editing /etc/X11/xorg.conf. Look for the [FONT="Courier New"]Section "Device"[/FONT] part of the config file and just add these couple of lines:

[INDENT][FONT="Courier New"]Option    "VideoOverlay" "on"
Option    "OpenGLOverlay" "off"[/FONT][/INDENT]

The whole thing looks simiilar to this:

[INDENT][FONT="Courier New"]Section "Device"
        [INDENT]Identifier  "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"[/INDENT]
EndSection[/FONT][/INDENT]

Then just simply reboot or completely restart the graphical server.

I also believe instructions for Nvidia cards are lying somewhere around here.

---

### Post by kg4gyt on 2006-06-08
I can't seem to find anything on how to do that on an nvidia card, everywhere only refers to it concerning the ATI drivers.

---

### Post by gala on 2006-06-08
thanks traveller.ct. That worked great. =D>

---

### Post by oobuntoo on 2006-06-09
gala,

Is your video card Nvidia? My video card is Nvidia, and adding those options don't solve the problem. I think they are for ATI cards only.

---

### Post by kg4gyt on 2006-06-09
I'm having the same problem, I can't seem to find anything on this problem concerning an nvidia card, everything seems to reference ATI.

---

### Post by gala on 2006-06-09
[QUOTE=oobuntoo]gala,

Is your video card Nvidia? My video card is Nvidia, and adding those options don't solve the problem. I think they are for ATI cards only.[/QUOTE]


My video card is ATI

---

### Post by chinozinho on 2006-06-11
same problem here....
nvida card, same error wen i try to run tvtime...

---

### Post by dracan_lin on 2006-06-19
I didn't get an error msg, just an ugly green screen in tvtime-window...

---

### Post by jesus_gascon on 2006-07-07
I use:
xdtv -c /dev/video0 -noxv :-D

---

### Post by eagle101 on 2006-07-16
Thanks traveller.ct, this worked great for a Radeon 9600XT (w/ dual monitors!).
Now I need to search how to enable sound :)

---

### Post by eagle101 on 2006-07-16
Whoops, forgot tv card line out.  It's been a couple years since I had this thing installed.  Look!  I'm watching TV!

---

