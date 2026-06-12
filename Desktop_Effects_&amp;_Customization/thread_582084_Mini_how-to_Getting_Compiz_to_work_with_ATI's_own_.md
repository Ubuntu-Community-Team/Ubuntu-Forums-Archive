---
title: "Mini how-to: Getting Compiz to work with ATI's own drivers (Ubuntu 7.10)"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by googlah on 2007-10-19
Hey all,

Just wanted to share how I did to make Compiz work great with the real accelerated driver from ATI. Myself has a ATI X800. I first installed Ubuntu 7.10. Then I went to to Synaptic Package Manager and installed almost every package which started with "compiz".

Now, go to "Restricted Drivers Manager" and enable the drivers for your card. Reboot if necessary. Now you are supposed to be able to right click on the desktop, choose "change desktop background", choose tab "Visual effects" and choose any of the options. But this is where it get stuck.

To get around this, open up your xorg.conf located in /etc/X11/xorg.conf and find at the very last line
```

Section "Extensions"
        Option          "Composite"     "0"
EndSection

```
And change this value to 1.

Next up, fire up the console and install the package "xserver-xgl" by typing
```

sudo apt-get install xserver-xgl

```

Reboot and now you should be able to enable the desktop effects with the real ATI driver support. :)

---

