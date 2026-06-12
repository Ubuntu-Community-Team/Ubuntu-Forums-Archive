---
title: "MPlayer: small display"
date: 2006-04-15
forum: Desktop Environments
---

### Post by take_one on 2006-04-15
Dear all,

Can somebody tell me why MPlayer won't fully display a film on fullscreen? I mean the picture stays in the middle and the rest of my monitor is just black.

Do you know?

Thanks...

---

### Post by Perfect Storm on 2006-04-15
Try change video driver to xv in mplayer.

---

### Post by take_one on 2006-04-15
i just did and no luck... another idea?

---

### Post by Perfect Storm on 2006-04-15
Do you use ATI card?

---

### Post by taurus on 2006-04-15
Or try, from a terminal...
```

echo "zoom=yes" >> ~/.mplayer/config

```
Then, fire up gmplayer again...

---

### Post by take_one on 2006-04-15
to be honest, i dunno... can you tell me how can i check it?

---

### Post by taurus on 2006-04-15
Applications -> Accessories -> Terminal to open a terminal.  Then at the prompt, type
```

lspci

```

p.s.  Have you tried out my suggestion about "zoom=yes" thing from above???

---

### Post by take_one on 2006-04-15
[QUOTE=taurus]Applications -> Accessories -> Terminal to open a terminal.  Then at the prompt, type
```

lspci

```

p.s.  Have you tried out my suggestion about "zoom=yes" thing from above???[/QUOTE]


i did, but now i can't call, player anymore... i dunno what i did wrong...

---

### Post by take_one on 2006-04-15
this is what i got from lspci

0000:00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
0000:00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
0000:00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
0000:00:00.3 RAM memory: nVidia Corporation: Unknown device 01aa (rev b2)
0000:00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
0000:00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
0000:00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
0000:00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
0000:00:05.0 Multimedia audio controller: nVidia Corporation: Unknown device 01b0 (rev c2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
0000:00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
0000:00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
0000:01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)

---

### Post by take_one on 2006-04-15
hey good... i got it... it works now... it opens up fully monitor size, but the film moves second by second... it's very actually slow...

---

### Post by take_one on 2006-04-15
THANKS GUYS, i got it... it's working just fine... thanks to both of you...

---

### Post by taurus on 2006-04-15
Good.  Looks like you have an nVidia card and if you haven't installed nVidia driver for your video card, check out this post and install it.  Pictures will look better and you can use the 3d accelerator on your card as well...  ;) 

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by dnccnd on 2006-04-16
[QUOTE=taurus]Or try, from a terminal...
```

echo "zoom=yes" >> ~/.mplayer/config

```
Then, fire up gmplayer again...[/QUOTE]

I used this code and it worked perfectly! :-D 

Thanks a lot!

---

