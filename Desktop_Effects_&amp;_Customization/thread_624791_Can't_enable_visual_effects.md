---
title: "Can't enable visual effects?"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by valkyr47 on 2007-11-27
Im new to this whole Ubuntu thing, and i like it so far, but one thing that sounds neat are the visual effects found by right clicking on the desktop and there is off, normal, and advanced... neither normal or advanced work for me, my visual effects are set to off and i cant figure out whats going on

it simply says "cannot enable visual effects" after hesitating for a few seconds

what gives?

---

### Post by Ub1476 on 2007-11-27
First post your graphic card:

```
lspci | grep VGA
```

And this might help too:

```
compiz
```

(copy/paste into terminal)

---

### Post by valkyr47 on 2007-11-27
_**lspci | grep VGA:**_
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)

**_compiz_**
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 


Thanks for any help you can offer, im sorry if this has been asked before or a mundane question, its just that i am a complete noob (first time in Ubuntu yesterday)

---

### Post by erfahren on 2007-11-27
enable ATI's proprietary driver (fglrx) if you haven't yet. System > Administration > Restricted Drivers Manager

when you enable Visual Effects you should be prompted to install XGL. If not you need to install the xserver-xgl package through the Synaptic Package Manager. (you'll need to restart the X Window System afterwards - Ctrl+Alt+Backspace). Then try enabling them.

---

### Post by valkyr47 on 2007-11-27
i just went to the restricted driver manager like you said and there is nothing there for ATI or my video card, just two entries for the modem...

---

### Post by Ub1476 on 2007-11-27
Your graphic card doesn't support restricted drivers very well, and slightly few problems with the open source drivers too, but it's getting better. There's a good guide [HERE]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually"), although it might seem a bit tricky. Just make sure you read the instructions carefully:)

---

### Post by hotrod6657 on 2007-12-30
erfahren:

Thank you so much for posting that mini how to!!!  I've been trying to enable visual effects with my ATI card forever and this is the first time that it's worked and didn't break my system, you rock :guitar:

Now i think i'll try and see if the same method  will work on the Alpha 2 of Hardy :D

Thanks again, happy New Year! lol

---

