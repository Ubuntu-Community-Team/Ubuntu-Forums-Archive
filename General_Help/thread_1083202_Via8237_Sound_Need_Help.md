---
title: "Via8237 Sound: Need Help"
date: 2009-02-28
forum: General Help
---

### Post by GuiGuy on 2009-02-28
My wife's computer died yesterday. I replaced the motherboard from an older ASUS K8MX box I had laying around. The sound is onboard VIA8237

I cannot get sound out the box. Following the [troubleshooting guide]("https://help.ubuntu.com/community/SoundTroubleshooting") I get:

> 
cat /proc/asound/modules
0 snd_via82xx


The card seems to be physically installed. lspci reports

> 
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ASUSTeK Computer Inc. Device 810d
        Flags: medium devsel, IRQ 22
        I/O ports at b400 [size=256]
        Capabilities: <access denied>
        Kernel driver in use: VIA 82xx Audio
        Kernel modules: snd-via82xx






aplay -l gives me

> 
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



The alsamixer visually reports all is well. Nothing is muted.

Finally, if I load a desktop off the livecd, sound works. I have to conclude the hardware is OK. 

So, I am back to "check your settings" but not sure what else I should do.

As I wrote, "Help"

T.I.A.

---

### Post by GuiGuy on 2009-03-01
Anyone?

---

### Post by otaviofcs on 2009-04-21
have you found the solution? I'm experiencing a similar problem. I'm using 8.10 and I also have this:

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
**00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)**
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)

as you can see. I'm able to hear some sound. But just some. It's **too low**, despite the fact that all my controls are set to 100% (see the attachment). It use to work until a recent update (I think it stops working 2 weeks ago).

I've already tried this post:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

But stills nothing. In 2 days more I'll upgrade to 9.04, but it's, at least, an awkward behavior.

Any luck? Any clue?

---

### Post by GuiGuy on 2009-04-21
> **otaviofcs said:**
> have you found the solution? I'm experiencing a similar problem.

Any luck? Any clue?

Sorry, I had posted the solution to my problem, but elsewhere :(

Anyway, I was using the ALSAMIXER to check the settings. It told me everything was good, but still no sound. 

Then, more out of desperation than clear thinking, I started the GNOME ALSAMIXER. It was telling me that the main volume was muted!!?? This despite everything else telling me otherwise. 

I checked all settings with the GNOME ALSAMIXER and all was well.

As an aside, I have had the same issues on other PCs. In each case the GNOME MIXER solved it for me.

[See here for my other thread on the topic]("http://ubuntuforums.org/showthread.php?t=1084467").

---

