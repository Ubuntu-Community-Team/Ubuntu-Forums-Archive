---
title: "Cinnamon miniature GUI in 4k"
date: 2017-04-04
forum: Desktop Environments
---

### Post by Blix775 on 2017-04-04
So I installed Xubuntu and Cinnamon on top of it. A couple of days ago I bought a 4k display and now the launch bar and the menus look too small. I would like to know how to increase their size so I can actually read the words and not misclick while using Cinnamon. I don't want to have to reinstall just for that.

---

### Post by SeijiSensei on 2017-04-04
Do you have a [video adapter that supports 4K]("https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&IsNodeId=1&Description=4k%20video%20card&bop=And&Order=PRICE&PageSize=60&N=600486270")?  Just changing the monitor won't help if the adapter doesn't support that resolution.  

If you do have a 4K adapter, what chipset does it use?  I'm guessing you would need [proprietary drivers]("https://www.google.com/search?client=ubuntu&channel=fs&q=nvidia+4k+linux&ie=utf-8&oe=utf-8") to make this work.

---

### Post by Blix775 on 2017-04-05
I have a GTX 970. The Cable is 4k and Windows allowed me to change the GUI size so that it would look bigger. I just need to find the same feature in Cinnamon.

---

### Post by SeijiSensei on 2017-04-07
Did you install the proprietary driver from NVIDIA?  The open-source nouveau driver may not support all the available resolutions.

---

### Post by Skaperen on 2017-04-08
since 4k has smaller pixels, any object with a *fixed size in pixels* will be smaller in the whole display.  what is needed is to increase the size of such objects to a *greater number of pixels*.  this is like going from 640x480 to 1920x1080.  *the font size might also need to be increased*.  image viewers should have a zoom capability to handle a range of image sizes.  what is useful to know is where (in the settings) to set the sizes of various things in Cinnamon or whatever DE one is using.  my display is 1824x1026.  i bet i am the only one with that size.

---

### Post by Bucky Ball on 2017-04-08
Additional Drivers and install the (recommended) driver. Reboot.

In apps you should now have the NVidia config app. Open that, select the 4k monitor and change the display resolution to 4096x2160.

Sorry can't give more precise details, but not on my machine at the moment (running a GTX 970).

---

