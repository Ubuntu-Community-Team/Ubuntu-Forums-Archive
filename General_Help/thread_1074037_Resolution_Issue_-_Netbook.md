---
title: "Resolution? Issue - Netbook"
date: 2009-02-18
forum: General Help
---

### Post by mistabroadway on 2009-02-18
I have the Acer Aspire One and I just installed 8.10 on it.  The resolution is set right but the bottom bar is half covered.  How would I go about adjusting the screen position?

---

### Post by CKDewey on 2009-02-18
Do you mean the bar is off the bottom of the screen? Try adjusting the refresh rate...

--
Tom

---

### Post by mistabroadway on 2009-02-19
I'm unable to change the refresh rate from the screen resolution.  My bottom bar is still half covered.

---

### Post by CKDewey on 2009-02-19
Do you mean refresh rate is not an option under System-->Preferences-->Screen Resolution?

Such as can be seen here:

[http://technical-itch.co.uk/wp-content/uploads/2007/04/screenshot-screen-resolution-preferences.png](http://technical-itch.co.uk/wp-content/uploads/2007/04/screenshot-screen-resolution-preferences.png)

---

### Post by mistabroadway on 2009-02-19
It's an option but its set to 58hz and there are no other options.

---

### Post by CKDewey on 2009-02-19
According to Acer's website there are two models; an 8.9in screen and a 10in screen, but both use 1024 x 600 resolution. Is this the resolution indicated in your display settings?

---

### Post by CKDewey on 2009-02-19
Also, do your /etc/X11/xorg.conf display settings match the ones in this guide:

[https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One](https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One)

---

### Post by mistabroadway on 2009-02-22
That link is dead.

---

### Post by Merk42 on 2009-02-22
> **mistabroadway said:**
> That link is dead.

Link works for me:
> 
(copied from Debian Acer Aspire One Help) When running under X, the native/optimum resolution is 1024x600 (standard widescreen ratio). The default X11 configuration will give you fonts that are too large for this resolution - You can add the following line to the "Monitor" section of your "/etc/X11/xorg.conf" file:

      DisplaySize 195 113 

And add the line:

      Option "NoDDC" 

to the "Device" section.

That sets the resolution to the correct 96 DPI.



---

### Post by mistabroadway on 2009-02-27
Good deal, I'll take a look when I get home.  Thanks.

---

