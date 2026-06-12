---
title: "moving apt windows"
date: 2006-05-01
forum: Desktop Environments
---

### Post by morequarky on 2006-05-01
In ubuntu, when I move a application window around the screen, there is this tail of half drawn "window" behind it.  The desktop refreshes enough so the tail goes away pretty fast, but it is still bothering me.  Is my on-board graphics not ubuntu compatible?  Is there a setting that is set wrong?  I don't like the tail.

When I minimize a program the same tail effect happens.  Is there a way to turn that off?

Thanks

note:  There are some new newbie post on the following thread including my a post from me.  No one has answered them so I am assuming no one knows the answer. [http://www.ubuntuforums.org/showthread.php?t=142481]("http://www.ubuntuforums.org/showthread.php?t=142481")

---

### Post by geek.de.nz on 2006-05-02
Maybe your graphics card is not installed properly. I get a "tail" too but it's hardly noticeable, because I got the NVIDIA drivers installed. What graphics card do you have? Do you know? If not, post the output of:
```

sudo lspci

```
here please. Maybe it's easier to help then. Also, check if you have a lot of overhead in your graphics settings (eye candy) and reduce it. What specs does your computer have?

---

### Post by morequarky on 2006-05-02
I don't know how to turn off all the eye-candy or reduse the amount of eye-candy I have.  What file do I modify?  Where are the settings for that?

I am using an on-board graphics "card".

My system is a 64bit 2.8ghz intel with 512RAM.  I run 32bit ubuntu breezy.  I'll install 64bit later when some stuff is more supported.

anyways...the output of "sudo lspci"

0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0314
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1314
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2314
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3208
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4314
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7314
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01)


Hope that helps.

---

### Post by geek.de.nz on 2006-05-02
Seems like  
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01)
is not supported. Try googling for it and/or your mainboard id and support for Linux. Other than that I don't know why it should be so slow with hardware like yours.

---

### Post by DoktorSeven on 2006-05-03
While it's best to get things running quicker, if you really need to reduce Gnome's resources, open the Configuration Editor (since I don't run Gnome, I can't remember what menu it's under, but running **gconf-editor** from gnome-terminal should work) and navigate to:

/ -> apps -> metacity -> general

On the right find "reduced_resources" and click the checkbox beside it.

Moving/minimizing/resizing windows should be a bit snappier now since Gnome won't redraw the whole window as you move or resize it, just when you stop.

---

