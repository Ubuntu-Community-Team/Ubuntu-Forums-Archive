---
title: "help with compiz fusion/awn"
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by nofear45465 on 2007-08-15
i have a question about avn and compiz fusion. for somereason i cant get any of my compiz fusion effects to work, and when i launch AWN it just looks like this [[IMG]http://img457.imageshack.us/img457/1620/screenshotdn3.th.png[/IMG]](http://img457.imageshack.us/my.php?image=screenshotdn3.png) with a huge black blob as you can see from the image. im sorry if this is a common answer i am a 100 percent noob to Ubuntu. BTW i am trying to sort of achieve some mac features, like expose and the dock and whatnot, but dont really want an exact clone.  my main computer uses OSX and i would like Ubuntu to have a little bit of an OSX feel to it. once again i just started using ubuntu about a week ago so when you respond try not to be too advanced. thanks.

---

### Post by EXCiD3 on 2007-08-15
When AWN makes a bar at the bottom like in your screenshot it just means that you dont have a Compositing Window Manger, such as Beryl/Compiz/ComizFusion running. You are using Metacity, Gnome's default window manager. You need to run Compiz Fusion in order for this to work correctly.

If you have the Compiz Fusion Icon installed you can change the window manager by right-clicking on its icon in the taskbar and selecting the correct window manager. This could possibly be caused by not having Compiz Fusion autorun upon login.

There is a lot of good information in this thread about using Compiz Fusion: [http://ubuntuforums.org/showthread.php?t=481615&highlight=howto+compiz+fusion]("http://ubuntuforums.org/showthread.php?t=481615&highlight=howto+compiz+fusion"). Read through it and you may find some useful information.

---

### Post by petit.padavoine on 2007-08-15
Does your system support Compiz Fusion at all?

```

glxinfo | grep rendering

```

You should get Direct rendering: Yes.

If you don't, your system doesn't support compiz fusion (or you don't have the appropriate drivers / configuration)

What graphics card are you using?

---

### Post by nofear45465 on 2007-08-20
it said no for direct rendering. im not sure which graphics card im running. is there a way to check without cracking open the pc?

---

### Post by miggols99 on 2007-08-20
Type lspci in the terminal and post the output

---

### Post by nofear45465 on 2007-08-20
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:09.0 Communication controller: Agere Systems LT WinModem
01:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

that is what it came back with. thanks for the help.

---

### Post by nofear45465 on 2007-08-23
bump. does anyone know if this setup is supported or if im SOL.

---

### Post by FuturePilot on 2007-08-23
Have you tried installing the compiz-fusion icon? It looks as though you're still using Metacity. I'm not sure whether Compiz-Fusion is crashing on startup or what. But you might want to give that a try. 
[http://ubuntuforums.org/showthread.php?t=497186]("http://ubuntuforums.org/showthread.php?t=497186")
Use the deb file in post #8

---

