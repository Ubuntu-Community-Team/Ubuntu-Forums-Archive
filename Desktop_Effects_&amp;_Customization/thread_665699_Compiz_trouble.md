---
title: "Compiz trouble"
date: 2008-01-12
forum: Desktop Effects &amp; Customization
---

### Post by Chepe on 2008-01-12
I've been struggling for some hours now to get compiz to work.
I have followed this guide:
[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

I'm running Ubuntu 7.10 on a dell xps m1330 with Nvidia GeForce 8400M GS. 

I got compiz up and running following the guide above, but then I had to reinstall ubuntu and now it doesn't work. That is, I mangage to install it and all, but when go to System->Preferences -> CompizConfig settings Manager and click it, nothing happens. 
Also, when I go to System ->Preferences ->Appearances -> Visual Effects and press Costum, nothing happens when i press the Preferences box to the right. 

I should maybe also mention that when I press Comstun under Visual Effects my keyboard shortcuts stop working. 

When entering 
```
compiz --replace
``` 
in a terminal I get this output:
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


Could someone please tell me what I'm doing wrong?

I appreciate all help!

---

### Post by Promaster91 on 2008-01-12
You need to get your graphic card driver. Check in System>Administration>Restricted Drivers Manger and see if you have your graphics card drive installed.

---

### Post by Chepe on 2008-01-12
My graphic card driver is installed, I checked the box to enable the driver before i started to follow the guide i linked to. And when following the guide I used envy to install the driver a second time.

---

### Post by Promaster91 on 2008-01-12
Here try to install the xserver-xgl package.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Chepe on 2008-01-12
Are you sure I should install that package? It seems to me that it's only valid for ati cards, and mine is Nvidia GeForce 8400m GS....

---

### Post by Promaster91 on 2008-01-12
Ok i am not use to ubuntu feisty. I think ubuntu feisty has a Synaptic Package Manger found in System>Administration>Synaptic Package Manger. Search for compiz. Then "completely remove" compizconfig-settings-manger. Once it removes it reinstall it and it should work. I had the same problem on my computer when I first started but I had a ATI graphics card. I am sorry for the mix up.

---

### Post by Chepe on 2008-01-12
Great success! :)
Now it works perfectly, I guess it really helped reinstalling it like you said!

Thanks for the help, I really appreciate it!

---

### Post by Promaster91 on 2008-01-12
No problem. Enjoy your new effects.

---

