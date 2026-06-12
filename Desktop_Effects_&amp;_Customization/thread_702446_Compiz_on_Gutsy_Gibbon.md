---
title: "Compiz on Gutsy Gibbon"
date: 2008-02-20
forum: Desktop Effects &amp; Customization
---

### Post by Grimbergen on 2008-02-20
Hello all,

I have a dell inspiron 1501 on which I installed Ubuntu Feisty and later I upgraded it to Gutsy Gibbon.
When I go to system ==> preferences ==> appearances ==>visual effects - custom it sais desktop effects could not be enabled. I already looked on several topics but the only thing they say is install Compizconfig settings manager. I installed everything and it works and the ATI driver is enabled.
P.S. My laptop works much slower since I installed all these features.

Thx in advance,
Grimbergen

---

### Post by chavanak on 2008-02-20
run compiz in terminal and give us the output. Also please mention which card you are using ati simply will not do

---

### Post by Grimbergen on 2008-02-20
256 MB ATI® Radeon® Xpress 1150 HyperMemory™
It's probably a stupid question but how do I run Compiz in terminal ?

---

### Post by Kubotaz4 on 2008-02-20
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5b60 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 


This was my output.  I cannot use the desktop effects.  PLEASE HELP!!

---

### Post by Grimbergen on 2008-02-21
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
Windowmanager waarschuwing: "" in de configuratiedatabase is geen geldige waarde voor toetsbinding "toggle_shaded"

This is What I get!
256 MB ATI® Radeon® Xpress 1150 HyperMemory™

---

