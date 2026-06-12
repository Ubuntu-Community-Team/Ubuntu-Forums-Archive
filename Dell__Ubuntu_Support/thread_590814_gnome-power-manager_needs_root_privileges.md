---
title: "gnome-power-manager needs root privileges?"
date: 2007-10-25
forum: Dell  Ubuntu Support
---

### Post by michael37 on 2007-10-25
Hi, I am running 64-bit Gutsy desktop (upgraded form Feisty 64-bit). I on my Dell Inspiron E1505/6400 and have a bizarre problem with my gnome-power-manager.

I described the problem [thread=590810]in Gnome forum in this thread[/thread].

Thanks for help in advance.

---

### Post by michael37 on 2007-11-03
OK.  More mysteries -- I bet this is specific to this Dell notebook model.

I spent a bit more troubleshooting and here is what I see.

*IF* gnome-power-manager is running (regardless whether it's root or myself), then monitor does not darken when lid is closed.

Instead, I get an error shown here in the bottom-right of the screen.

*IF I KILL* gnome-power-manager, then monitor DOES darken when lid is closed.  I have no idea which process does it since I don't see anything in the logs like dmesg.

P.S.  I misdiagnosed the problem earlier -- sudo gnome-power-manager does not even start gnome-power-manager daemon as easily verified by ps -ef command.

[IMG]http://i10.tinypic.com/4z09lkm.png[/IMG]

---

### Post by michael37 on 2007-11-03
I have Dell Notebook E1505 with just one native LCD screen.

Right now it tells me that DPMS is not supported...

```

(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SEC  Model: 3157  Serial#: 0
(II) fglrx(0): Year: 2006  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 95.4 MHz   Image Size:  303 x 190 mm
(II) fglrx(0): h_active: 1440  h_sync: 1504  h_sync_end 1536 h_blank_end 1744 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 906 v_blanking: 912 v_border: 0
(II) fglrx(0):  GR448^A154W1
(II) fglrx(0):  ^W&9Ei<91>Ãÿ^B^A
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):  00ffffffffffff004ca3573100000000
(II) fglrx(0):  00100103802115780a87f594574f8c27
(II) fglrx(0):  27505400000001010101010101010101
(II) fglrx(0):  0101010101014825a03051840c304020
(II) fglrx(0):  33002fbe100000190000000f00000000
(II) fglrx(0):  000000000078e6022300000000fe0047
(II) fglrx(0):  523434380131353457310a20000000fe
(II) fglrx(0):  00172639456991c3ff02010a20200030
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS

```

---

### Post by bluedragon436 on 2007-11-18
I have a not as nice Dell laptop (D610) and am having this same issue...  I have been working on trying to figure it out myself...with no such luck..

---

### Post by Linicks on 2007-11-18
Funnily enough, I moved to fluxbox on my laptop - and that has come such a long way, I built and installed on my desktop.

Then I needed a way for the desktop to dpms power save.  I sorted that using flubox/startup file.

Then I thought my Dell Inspiron 6400 doesn't do it either (?)  I use xlock when I leave it a bit, and suspend if I leave it for a while.  So fixed that up today, but only in fluxbox.

Anyway, try this which I used in the fluxbox/startup file.  Put in your rc.local file, perhaps as the last line to exec:

xset dpms 300 600 900

That == standby 300 secs (5 minutes), suspend 600 secs, OFF 900 secs.

See how you go.  But you NEED to ensure that it runs AFTER gnome-power-management is started to over-ride it's dpms 0 settings.

Nick

---

