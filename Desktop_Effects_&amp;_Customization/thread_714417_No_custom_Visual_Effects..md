---
title: "No custom Visual Effects."
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by Zummy on 2008-03-03
Many guides tell me to run compiz-fusion that I must go to System => Preferences => Appearance => Visual Effects, and click custom effects.  I click it, it loads and everything seems normal, then it goes back to None.

Anyone have any fixes? They don't say anything other than: "Desktop Effects could not be Enabled."

Thanks for the time and effort guys! :guitar:

---

### Post by bwang on 2008-03-03
Please post your system specs.

What does it say when you go to Terminal and run compiz?

---

### Post by Zummy on 2008-03-03
How do you do those in ubuntu (7.10) I'm fairly new and still grasping the ropes.

---

### Post by wabbster on 2008-04-03
Hi,

I'm having a similar situation here... This is what I get. when I try to run Compiz..


Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity


Any help would be appreciated.

Wabbster.

---

### Post by vonlogik on 2008-04-23
You may have to install Compiz. I didn't even have the option until I did

[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)

Also, I'm using the nvidia proprietary glx driver. To install those I simply ran 'sudo synaptic', then searched for nvidia. You'll see the nvidia-glx entry, click the box and choose install. (If you have an ATI or another card you will of course search for those drivers, not nvidia's)

Hope this helps.

---

### Post by Ni85 on 2008-04-27
I've solved this problem following a tutorial on the italian forum and editing the compiz file in /usr/bin/compiz

the first lines should look like these:

```
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real) 
```

sometimes there is a "local" in between usr and bin, and compiz name has no ".real" after it.

it worked fine for me, altough i'm still trying to figure out why i have no "custom" option on the visual effect tab.

---

