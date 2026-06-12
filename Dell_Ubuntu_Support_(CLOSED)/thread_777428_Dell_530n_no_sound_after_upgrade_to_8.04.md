---
title: "Dell 530n no sound after upgrade to 8.04"
date: 2008-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by javaben on 2008-05-01
I've seen multiple posts about other Dell systems having lost their sound, but none for the Inspiron 530n, which Dell sells configured with Ubuntu 7.10. 

I upgraded to the Hardy 8.04 LTS, and have experienced some problems (overall performance is down a LOT, CPUs running much higher in system monitor, typing sluggish even to this post).  The biggest problem right now is I have no audio at all.

I'm working my way through the posts for the other Dell systems, but even the Dell site doesn't show any 530n impacts, so wanted to identify there is an impact to 530n.

If anyone has any additional insight for the 530n, it would be appreciated.

Thanks,

JavaBen

---

### Post by javaben on 2008-05-01
Some additional info:

Ubuntu
Release 8.04 (hardy)
Kernel Linux 2.6.24-16-generic
GNOME 2.22.1

lspci
[INDENT]
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
[/INDENT]

sudo lshw -C sound
[INDENT]
 *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
[/INDENT]

Thanks!

---

### Post by javaben on 2008-05-01
Well, I have half of the problem solved.

The Dell Insiron 530N has two sets of audio out jacks; one on the front, another set on the back.  I normally use the rear set of jacks for my speakers, and headphones on the front set.

It appears the front audio panel is working, but not the rear.

When I look at the HDA Audio control, I no longer have any capability of setting the volume on the rear speakers; only the front speakers have a volume control slider.

When I use the HDA Audio Control panel, select Edit->Preferences, there are not any preferences for the rear speaker - just the front speaker.

Any ideas or suggestions?

JavaBen

---

### Post by mihashise on 2008-05-10
I had the same problem. 
I tried your suggestion and noticed as well that the front panel works well.
Under KMix --> Switches I switched the Front light and the loudspeakers (strangely at the back) begun to work. 
So it seems that Headphones means Front and Front means Back :)

Hope it will solve your problem too.

Miha (and Mozart behind)

---

### Post by javaben on 2008-05-12
Thanks for your suggestion, but I don't appear to have the same kmix view you have.  I didn't find kmix in my original install, so I pulled it down via the synaptic package manager.  It didn't show up with any launchers after the install, so I brought up a terminal session, and typed kmix, which launced it.  I don't know if I should have launched with any switches or not.

At any rate, kmix came up. Under the 'switches' tab, I have two (2) buttons: the first, labled 'Headphone' is currently yellow.  I've clicked that button, and it toggles between yellow and blank; blank gives no sound through front speakers, yellow gives sound through front speakers.  There is no output from rear plugs.  The other switchs is labled IEC958.  It is red.  Toggling this changes it from red to orange(?).  It does not influence the front, nor the back.  That's all the switch buttons I have under that tab.  I have three other drop down list boxes, labled 'Channel Mode (set to 6ch)', Input Source, and Input Source.  That's all of the items on the 'Switches' tab.

So it appears our kmixes behave differently?

---

