---
title: "Help with X : modules doesn't exist"
date: 2006-07-31
forum: Desktop Environments
---

### Post by SexyStud on 2006-07-31
Hi,

I recently installed Xubuntu on my old PC (for reference, graphic card is a Matrox Millenium G200 AGP 8Mb). However I don't seem to be able to get X to work. if I config through dpkg-reconfigure, the wizard only prompts me with 3 drivers to choose for the graphics: voodoo, neomagic and siliconmotion. None of them work. If I manually edit xorg.conf and change the driver to "mga" or "vesa", I get "(module doesn't exist, 0)" when I startx. What can I do to get X running properly here?

Also, my xorg.conf has some lines regarding a "eraser" device, using the module "wacom", which does not exist either. What is this wacom?

---

### Post by jasutton on 2006-07-31
You might need to:

```
sudo apt-get install xserver-xorg-driver-vesa
```

for the 'vesa' module to work.  I'm not sure why that wouldn't be installed, but I've never installed Xubuntu, so I'm not sure what it's default packages selection contains.

---

