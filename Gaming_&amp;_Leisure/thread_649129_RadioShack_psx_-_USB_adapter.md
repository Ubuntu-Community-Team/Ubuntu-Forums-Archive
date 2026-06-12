---
title: "RadioShack psx - USB adapter"
date: 2007-12-24
forum: Gaming &amp; Leisure
---

### Post by KB1LQC on 2007-12-24
I searched the forum but I was a bit confused on the answers (Especially recompiling the kernal)  to the playstation to usb adapters.  I just got epsxe to work so I found my old playstation to usb adapter I used years ago on windows (worked fine).  its a RadioShack "Playstation to USB adapter" with a little 5 inch USB pigtail and a 3 inch by 2 inch by about 1 cm thick black box with RadioShack on it an a red led just above that.

I believe it is recognized underUSB Game Device>  USB HID Interface> USB Game Device  However there is no input that I can see... anyone have any suggestions?

---

### Post by KB1LQC on 2007-12-24
OK so using jstest and jscalibrator I found that the adapter is working.  However the epsxe program is not recognizing my gamepad (Playstation Dual Shock 2).  [IMG]http://picasaweb.google.com/bstguitarist/Ubuntu/photo#5147677724922054002[/IMG]

As you can see there is no selection for my analog controller only the keyboard works...




Thank You,

KB1LQC

---

### Post by acoustibop on 2007-12-24
A few points, KB1LQC - Ubuntu usually puts your first joystick device at /dev/input/js0 (or increments the js0 number for additional devices), while many applications look for it at /dev/js0.  You can either configure your application to look at /dev/input/js0, or put a symlink to /dev/input/js0 in /dev.

Secondly, unless you're using Kubuntu and its included version of jscalibrator, get rid of jscalibrator.  It seems to have a nasty habit of disabling joystick controls while reporting that they work... You need to remove the jscalibrator configuration as well as the application, and some people find it necessary to reboot to re-enable their joystick.

And lastly, why not try [pSX Emulator]("http://http://psxemulator.gazaxian.com/")?  It's generally a far better Playstation emulator than ePSXe, which is looking rather long in the tooth by now.  And it seems to pick up controllers much better, and doesn't have the problems ePSXe does enabling and configuring analog controllers.

BTW if you want to enable an analog controller in ePSXe (it only supports one), AIR you need to use the PadJoy plugin, set the -analog switch on starting, and set the plugin for PCSX rather than ePSXe.

---

### Post by KB1LQC on 2007-12-25
> 
And lastly, why not try pSX Emulator? It's generally a far better Playstation emulator than ePSXe, which is looking rather long in the tooth by now. And it seems to pick up controllers much better, and doesn't have the problems ePSXe does enabling and configuring analog controllers.

Thanks!  Ya it works a LOT better! When I originally tried it the program would not open for some reason but pSX Emulator now works when I reinstalled it!  I found that ISO's work a lot smoother so Im making ISO's of my games but some are copy protected... any suggestions?   I mean, I own the game so I should be able to lol.

---

### Post by acoustibop on 2007-12-25
Absolutely, but since when did large companies care about your rights, KB1LQC?

The problem with copy or mod protected Playstation games is that the protection is not in the normal sectors of the CD, so you need to rip to a format that includes the subcode from the CD, either .ccd/.img/.sub or .mdf/.mds.  pSX can then read the subcode and, in most cases, defeat the protection.  Unfortunately, there are no applications for Linux that can do this: you need [CloneCD]("http://www.slysoft.com/en/") or [Alcohol]("http://www.alcohol-soft.com/"), and both are Windows only - they don't even run in Wine.  So, apart from those applications, you need to have access to a Windows installation.  Ripping CDs and DVDs is the only reason I keep one going...

You also need an optical drive that can read the subcode (generally, -RW drives are better than -ROM drives at this) properly, and good ripping technique - see the [HOW TO: Make Disc Images]("http://psxemulator.proboards54.com/index.cgi?board=rules&action=display&thread=1195746305") thread on the official pSX forum.

However, pSX does seem much better at reading games from CD than I remember ePSXe being, so you could try that for your protected games, as long as you have have a drive that will read the subcode.

Another alternative is to try ripping to .bin/.cue format and then patching the image, either directly, or by running the patch 'on the fly.'  A good way of doing this is with [Ultima's pSX Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263"), which is also a very useful way of starting pSX in its own right.  Remember that, to get successful results for patching, you need to have a properly ripped image and the correct patch for the specific version of the game - some patches just don't seem to work anyway... A good place for patches is [MegaGames]("http://www.megagames.com/").

pSX normally only needs one extra dependency over and above what's found in a standard Ubuntu (certainly Edgy, Feisty or Gutsy), and that's libgtkglext1 (in the repositories).  Apart from that, it needs a working 3D graphics card and a working soundcard.

---

