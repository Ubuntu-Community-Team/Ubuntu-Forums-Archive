---
title: "PCI address"
date: 2006-03-12
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-03-12
I'm trying to configure a dual head, but I don't know how to interprete the output of lspci to know the pci address of the second head of my ati card.
I think this are my two heads:
```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b62
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b72

```
The address for one of them in xorg.conf is PCI:1:0:0.
How do I get this from this output? And what's the address for the other one that I should put into xorg.conf? (Could it be PCI:1:0:1? I want to be sure)

---

### Post by Ramses de Norre on 2006-03-13
Anyone?

---

### Post by Ramses de Norre on 2006-03-16
bump

---

### Post by nalmeth on 2006-03-16
Not getting much response huh?
I would guess that sounds correct, but wouldn't guarantee it. Can you post a howto you might be following, or what you are supposed to be doing with this step? Don't really understand the situation

---

### Post by Ramses de Norre on 2006-03-16
I'm trying to set up a dual head configuration but I doesn't work out..
I need to specify the pci addresses for the heads in my xorg.conf so I thought maybe I've got the wrong pci address for my second head..
I couldn't find anything on the web on how derivating the syntax xorg uses for pci addresses out of this output.
This is just one thing I thought that could be wrong in my xorg.conf.

---

### Post by Ramses de Norre on 2006-03-18
Is there really no one on the forums who knows how to get to the pci address..?:???:

---

### Post by claes on 2006-03-18
Not sure if I understood the question but is it this your wondering about. From my /etx/X11/xorg.conf
--- snip ---
Section "Device"
        Identifier      "internal"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
--- snip ---

The BusID I got from lspci.

Claes

---

### Post by Ramses de Norre on 2006-03-18
But if lspci says 0000:01:00.1, then what's the value you need to enter in xorg.conf?

---

### Post by deavik on 2006-03-18
Jusdt wanted to confirm for you that yes, the address of the second device is PCI:1:0:1

edit: but I'm a little confused as to how that works though. I have my PCI devices as 1:0:0 (network) and 1:2:0 (video) with the middle slot empty AFAIK. I'm not a hardware expert, so ...

---

### Post by Ramses de Norre on 2006-03-19
Ok thanks, I don't really understand those addresses neither.

---

### Post by ranf on 2006-03-19
You can also let X scan for PCI addresses:
```
sudo X :1 -scanpci
```

It lists them in the format needed for the xorg.conf.

---

### Post by Ramses de Norre on 2006-03-19
Ow thanks! Didn't know of that.

---

