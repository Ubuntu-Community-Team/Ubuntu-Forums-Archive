---
title: "beryl-integrated intel 82801 chip"
date: 2007-08-17
forum: Desktop Effects &amp; Customization
---

### Post by posingaspopular on 2007-08-17
Hey all. I'm having trouble figuring out how to do anything in terms of desktop effects for Kubuntu Fesity Fawn (7.04) on an Intel Chip. I haven't found any guides online that have been what I've needed. Basically, all I have is

'sudo apt-get install beryl' 

Help?

-Eddie Martinez

---

### Post by miggols99 on 2007-08-17
Intel cards work out of the box. Have you edited your xorg.conf to enable AIGLX? If not you will need to:

```
gksudo gedit /etc/X11/xorg.conf
```

You xorg.conf will appear. Now add this at the end:

```

Section "ServerLayout"
         Option         "AIGLX" "true"
EndSection

```

And this:

```

 Section "Extensions"
       Option         "Composite"   "Enable"
 EndSection

```

And these to your device section:

```

 Section "Device"
       ......
       Option      "XAANoOffscreenPixmaps" "true"
       Option      "DRI"     "true"
       ..... 
EndSection

```

and

```

 Section "DRI"
       Mode 0666
EndSection

```

Remember to backup your old xorg.conf!!

---

### Post by posingaspopular on 2007-08-17
I have not done, any of that. thank you. how do I backup my xorg.conf file and where do I back it up to?

---

### Post by miggols99 on 2007-08-18
Open up nautilus as root:

Alt F2 >> gksudo nautilus

Browse to /etc/X11/

Copy the file xorg.conf

Open a new window

Browse to your home directory /home/<insert username here>

Paste the file.

If X dies the next time your reboot, you can restore the old xorg.conf by:

```
sudo mv ~/xorg.conf /etc/X11
```

---

