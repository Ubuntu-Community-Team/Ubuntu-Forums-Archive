---
title: "Screen isn't composited. AWN wont start"
date: 2007-11-28
forum: Desktop Effects &amp; Customization
---

### Post by rh-penguin on 2007-11-28
hi,

I've got an integrated ATI Radeon X1250 graphics card inside my Asus M2A-VM mobo.
I've installed AWN+Compiz+xserver-xgl package but AWN just wont start it gives me: ```
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

```
Can anyone please help me out? 
lspci output is:```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```I'm running Ubuntu Gutsy 7.10** 64 bit!**

---

### Post by mamlouk on 2007-11-28
Which ATI driver are you using?

---

### Post by rh-penguin on 2007-11-28
hmm, thats strage it works now. 
Ive got the ATI accelerated graphics driver (System>Administration>Restricted Drivers Manager)
But for some reason all of my windows are missing the tittle bar....... The topic is there and minimize,maximise, etc is there.......... but no tittle bar.

---

### Post by mick222 on 2007-11-28
same problem no title bar when i run compiz Ati 9600 athlon 64 32bit gutsy .

---

### Post by rh-penguin on 2007-11-28
i also get the following in shell when i start awn ```
cookie@ubu1:~$ avant-window-navigator &
[1] 6381
cookie@ubu1:~$ Screen is composited.
APPLET : /usr/lib/awn/applets/filebrowser.desktop
APPLET : /usr/lib/awn/applets/trash.desktop
APPLET : /usr/lib/awn/applets/digitalClock.desktop
APPLET : /usr/lib/awn/applets/mimenu.desktop
return
/usr/lib/awn/applets/digitalClock/dgTime.py:23: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  self.draw_clock()
/usr/lib/awn/applets/digitalClock/dgTime.py:23: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  self.draw_clock()
/usr/lib/awn/applets/digitalClock/dgTime.py:23: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  self.draw_clock()
68528
/usr/lib/awn/applets/digitalClock/digitalClock.py:113: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main ()
/usr/lib/awn/applets/digitalClock/digitalClock.py:113: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  gtk.main ()
/usr/lib/awn/applets/digitalClock/digitalClock.py:113: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  gtk.main ()

```

And also, i've bin trying to drag and drop stuff into the awn bar but it wont let me. When i drag something over the bar it does show a + sign but it wont add

---

### Post by rh-penguin on 2007-11-29
can someone help me out?

---

