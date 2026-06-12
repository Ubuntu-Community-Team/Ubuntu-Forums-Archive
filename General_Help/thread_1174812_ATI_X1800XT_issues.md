---
title: "ATI X1800XT issues"
date: 2009-05-31
forum: General Help
---

### Post by davbren on 2009-05-31
Hey all, I am having problems with my ATI X1800XT card. I can't enable compiz otherwise I get the white screen of death. Is there anything I can do?

---

### Post by jonathanysp on 2009-05-31
did you install drivers for your graphics card? oh and what does the terminal say when you run compiz --replace?

---

### Post by davbren on 2009-05-31
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 1002:7100 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
```


I installed the drivers yh, but it seems that for some reason they aren't active. :(

---

### Post by davbren on 2009-06-20
I don't suppose anyone has found out a solution to this?

---

### Post by masux594 on 2009-06-20
Try with this solution..

```
*sudo gedit /etc/xdg/compiz/compiz-manager*
```and at the end of the file add this line [if dont'exist yet]
```
SKIP_CHECKS="yes"
```Sysc, A

P.s. reboot after added the line and saved the file!

---

### Post by davbren on 2009-06-20
Hmm, no luck I'm afraid, I'm still getting a white screen.

What did this mean?

> 
Sysc, A

cheers.

---

### Post by masux594 on 2009-06-21
white screen.. .. Hmm,  i've never heard about a white screen.. .. Black, but not white.. ..
"Sysc"?? is a quote from my favourite anime.. many people ask to me the same question, try to find yourself the answer.. i give to you a clue =P 

Sysc, A

P.s. For the problem i'm going to googling this afternoon!

---

### Post by Legace on 2009-06-21
Ubuntu Jaunty (with Xserver 1.6 and FGLRX 9.3+) dropped support for cards prior to the 2xxx series. Unfortunately, your card isn't supported by Jaunty.

For 3D acceleration/composting, you'll have to either downgrade to 8.10 or wait till good enough open-source drivers are made.

---

### Post by masux594 on 2009-06-21
> **Legace said:**
> Ubuntu Jaunty (with Xserver 1.6 and FGLRX 9.3+) dropped support for cards prior to the 2xxx series. Unfortunately, your card isn't supported by Jaunty.
For 3D acceleration/composting, you'll have to either downgrade to 8.10 or wait till good enough open-source drivers are made.

there's no need to downgrade ubuntu to run compiz with this video card .. I have a 1xxx ATI video cards too and with RadeonHD drivers, all works fine.. compiz enabled with various effect.. Need a guide to install the RadeonHD drivers?

Sysc, A

---

### Post by davbren on 2009-06-21
> **masux594 said:**
> there's no need to downgrade ubuntu to run compiz with this video card .. I have a 1xxx ATI video cards too and with RadeonHD drivers, all works fine.. compiz enabled with various effect.. Need a guide to install the RadeonHD drivers?

Sysc, A

That would be great yh, cheers.

---

### Post by masux594 on 2009-06-21
this is the [RadeonHD guide]("https://help.ubuntu.com/community/RadeonHD") that i follow to enable compiz with all the fashion features =)

Sysc, A

---

### Post by masux594 on 2009-06-30
No results?

Sysc, A

---

