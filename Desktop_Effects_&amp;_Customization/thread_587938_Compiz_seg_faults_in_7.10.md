---
title: "Compiz seg faults in 7.10"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by malaeum on 2007-10-23
Hello,

I have been trying to get compiz working on my 7.10 install of Kubuntu. I have tried many methods and followed many guides, in the end each time compiz --replace results in a segmentation fault. I think the best guide I found was here...[http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users#](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users#)

I followed that guide to the letter understanding everything I have done along the way. I am running Kubuntu 7.10 X86_64. I have an nVidia 8600 GT card running the 100.14.X drivers installed via Envy. 

I have tried running emerald --replace and it doesn't do anything. Running it from a prompt produces nothing, I have to ctrl+c to get back to the prompt otherwise it just sits there. 

Here is the output of trying to start compiz --replace:
```
mmschnei@benzene:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 04:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
Segmentation fault (core dumped)
Not initializing the Gtk-Qt theme engine

```



I have read that ati-driver users are supposed to install and use xserver-xgl, I just went ahead and tried this, interestingly enough this did not use my nvidia driver but it did allow compiz to run flawlessly. Now I need to figure out how to get it working wtih my driver. I have since uninstalled xserver-xgl and am back to xorg. I guess I need to figure out how to enable xgl in xorg...

Any one else having these problems?

---

### Post by obsrv on 2007-10-23
Try to remove emerald and install compiz-kde :)

---

### Post by malaeum on 2007-10-23
> **obsrv said:**
> Try to remove emerald and install compiz-kde :)

Tried that, a few times actually.  =\

I think I have figured it out. I failed to mention that I am running dual monitors in my previous post. I had them setup to run as seperate X servers with Xinerama enabled. As soon as I switched to nvidia's "twinview" and ran compiz came up like a charm.

---

