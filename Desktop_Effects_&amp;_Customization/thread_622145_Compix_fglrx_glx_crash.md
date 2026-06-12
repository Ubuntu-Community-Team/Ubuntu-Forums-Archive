---
title: "Compix fglrx glx crash"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by mistermax on 2007-11-24
I am running an ATI x-1350 and have got Compiz working, looks great and really like it.

However if I try to run anything like fglrxgears or any gl application or game, x crashes and I need to log back in.

I've attached my xorg and here is my fglrxinfo results...

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 / X1550 Series
OpenGL version string: 2.0.6958 Release


Is there anything I can do to fix this?

---

### Post by tombean on 2007-11-24
Hi I had the same problem while setting up WoW. This fix here made it work for me.

Apparantly it causes sudden crashes caused through the fglrx driver to stop.
Insert this to your /etc/X11/xorg.conf file under the "device" section which refers to fglrx.

```

	Option	    "Capabilities" "0x00000800"
	Option	    "UseFastTLS" "0"
	Option	    "KernelModuleParm" "locked-userpages=0"

```

Regards,
tombean

---

### Post by mistermax on 2007-11-24
Thanks,

that seems to do some crazy stuff though- tested the change with fgl_glxgears -

it didn't open gears, instead I noticed that strange redraw thing where if you move the window about, you get a visual echo thing... Hard to explain without recording I suppose.

In my xorg the device is listed as this
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:2:0:0"
EndSection

although I know it is a PowerColor ATI x-1350 512 meg card.

I'm going to try changing the "UseFastTLS" switch to 2 which apparently uses it on demand rather than fast or fastest.

Any other suggestions would be great.

ta

---

### Post by mistermax on 2007-11-24
the output I get from fgl_glxgears when using the 2 switch is:

Using GLX_SGIX_pbuffer
Error: couldn't get fbconfig

---

### Post by mistermax on 2007-12-05
bumping this as perhaps someone else has seen similar?

I find that lspci |grep vga returns my card type:

02:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]

I'm using fglrx, but is this another driver I should be considering?

---

### Post by mistermax on 2007-12-12
Attaching the last X.org log crash I encountered.

If I am missing a thread that has a fix for this, someone please point me at it!

(Has the search facility changed on this site? Seems to block searches for 15 seconds between)

---

### Post by mistermax on 2007-12-12
max@scunner:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
Error: couldn't get fbconfig

---

### Post by mistermax on 2007-12-18
Rapidly coming to the conclusion there isn't a decent fix for ATI, basically if you've got a card it is tough.

:mad:

---

