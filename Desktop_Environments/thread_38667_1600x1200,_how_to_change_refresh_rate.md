---
title: "1600x1200, how to change refresh rate?"
date: 2005-06-01
forum: Desktop Environments
---

### Post by GTKpower on 2005-06-01
I've got my desktop at 1600x1200 resolution, but the highest refresh rate option is 75hz.

I've got a Radeon 8500 128mb, and I KNOW it is capable (easily) of running 1600x1200 at 85hz.

How can I force an 85hz refresh rate for my Hoary desktop?

---

### Post by glasscleaner on 2005-06-01
maybe your screen cant support this refresh rate at this resolution.

can you get 85hz with this resolution in windows?

---

### Post by GTKpower on 2005-06-01
Whoops . . . . you're right.  Damn.  My monitor's manual lists 76hz as the highest supported rate at 1600x1200, with the "ideal" rate being 85hz at 1280x1024, which GNOME supports.

Well, question asnswered, then.  It's just that I could have sworn that my monitor (NEC FE950+) could pull of 85hz at 1600x1200.

Thanks anyway for the reply, which reminded me.

---

### Post by az on 2005-06-01
Select the xserver-xorg package in synaptic.  Use the drop-down menu to (re)configure your package.

---

### Post by GTKpower on 2005-06-01
Well, I already had the Xorg-xserver package.  So, I configured it, went through a list of options, and at sonme point, selected 1600x1200 at 85hz as the "best" video mode.  I'll reboot to see if this had any effect.

---

### Post by m0biu5 on 2005-06-01
Just for reference, here is a how to that I found helpful when dealing with resolutions and refresh rates. There is some good info there!  :)

---

### Post by GTKpower on 2005-06-01
Well, I confirmed it.

If your monitor is unable to dispaly a certain res. at a certain refresh rate, you can't force it to do so, xorg-xserver or not.  Won't work, at least not through the xorg-xserver.

---

### Post by skoal on 2005-06-01
The specs on my monitor:

HorizSync       30.0 - 107.0
VertRefresh     48.0 - 120.0

1280x1024@85Hz is the highest validated mode at that resolution.

* However, gtf is yo daddy...

skoal@morpheus://~ $ gtf 1280 1024 95 -x

  # 1280x1024 @ 95.00 Hz (GTF) hsync: 102.79 kHz; pclk: 180.91 MHz
  Modeline "1280x1024_95.00"  180.91  1280 1376 1520 1760  1024 1025 1028 1082  -HSync +Vsync

I add that to my Monitor section in 'xorg.conf'.

At least in XFCE (since it uses the RandR extension), I can select that video mode from Settings->Display Settings.  I'm running 1280x1024@95Hz.  My monitor supports this with it's horiz range, so why not use a higher refresh rate.  You should be able to choose any refresh rate at any resolution provided it falls within your horiz range.  I could have tried 1280x1024@100, but it just falls outside the 107.0 horiz limit.

who's yo daddy?! validate >>this<< nvidia...

---

### Post by GTKpower on 2005-06-01
My horizontal range is 30 - 96, it appears.

I suppose I can try that and make the appropraite addition to the xorg conf file.

BUT . . . is it actually *safe* to go beyond the officially supported (hardware) rates?

---

### Post by bored2k on 2005-06-01
[QUOTE=GTKpower]My horizontal range is 30 - 96, it appears.

I suppose I can try that and make the appropraite addition to the xorg conf file.

BUT . . . is it actually *safe* to go beyond the officially supported (hardware) rates?[/QUOTE]
 You might just break your monitor. Simple as that. Remember Windows's "Going beyond might break stuff" ? It applies.

---

