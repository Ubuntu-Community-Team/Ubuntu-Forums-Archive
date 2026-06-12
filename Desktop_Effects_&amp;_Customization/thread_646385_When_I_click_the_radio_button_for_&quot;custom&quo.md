---
title: "When I click the radio button for &quot;custom&quot; effects, it says..."
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by joesmith1234 on 2007-12-21
"Desktop effects could be enabled"

I just did a fresh reinstall of gutsy gibbon and I am trying to start from scratch.

I have installed the ccsm window manager, but I can't enable the desktop effects.

I think it might have something to do with my graphics card driver... this is an older PC (3 years plus)...  how do I find out what my graphics card is and how do I find out if I have the appropriate driver?

Also for what it's worth:
```

thuskins@thuskins-desktop:~$ glxinfo | grep direct
direct rendering: Yes
thuskins@thuskins-desktop:~$ 

```

---

### Post by joesmith1234 on 2007-12-21
More info:

```

thuskins@thuskins-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0113 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

```

---

### Post by joesmith1234 on 2007-12-21
Fixed with the following
> 
go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.


From: [http://ubuntuforums.org/showthread.php?t=582207&page=2](http://ubuntuforums.org/showthread.php?t=582207&page=2)

---

