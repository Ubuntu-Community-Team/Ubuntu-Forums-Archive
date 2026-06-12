---
title: "can't increase resolution"
date: 2005-12-24
forum: Desktop Environments
---

### Post by polloz on 2005-12-24
hello, my problem is this. i've installed breezy on a pentium III 500 mhz with 256 ram and a geforce 2 mx 64mb. the instalation went perfectly and i'm currently typing from ubuntu, but the thing is that the maximum resolution i can set is 1024 x 800. i have a 17 inch monitor, and i want a 1280 x 1024 resolution, something that my monitor and my video card will sure allow me to do, but unfortunately i can't increase the resolution further than 1024 x 800.
what could be the problem? thanks,
pollo

---

### Post by dcstar on 2005-12-24
[QUOTE=polloz]hello, my problem is this. i've installed breezy on a pentium III 500 mhz with 256 ram and a geforce 2 mx 64mb. the instalation went perfectly and i'm currently typing from ubuntu, but the thing is that the maximum resolution i can set is 1024 x 800. i have a 17 inch monitor, and i want a 1280 x 1024 resolution, something that my monitor and my video card will sure allow me to do, but unfortunately i can't increase the resolution further than 1024 x 800.
what could be the problem? thanks,
pollo[/QUOTE]
Try (in a user terminal):

sudo dpkg-reconfigure xserver-xorg

and let it auto-select with the "Simple" option on the screen res section, then do CTRL-ALT-Backspace to restart the X-server with the changes, otherwise run it again and try the other options that allow you to specify more yourself.

---

### Post by afhp on 2005-12-24
The problem is that XWindow doesn't really know what your monitor is capable of. 

If you run dpkg-reconfigure xserver-xorg, it should prompt you at some point for your monitor's refresh rates ; look up your monitor's manual to put in the right values. 

If you look directly in /etc/X11/xorg.conf, that's in the "Monitor" section : 
```

Section "Monitor"
        Identifier      "Hyundai V773"
        Option          "DPMS"
        DisplaySize     305 229
        [B]HorizSync       30-70
        VertRefresh     50-150[/B]
EndSection

```

Adjust HorizSync and VertRefresh according to your monitor's specs.

Also check the "Screen" section, "Display" subsections and make sure you have the higher resolutions listed there:
```

        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection

```

---

### Post by matsberglund on 2005-12-25
Just registered to say "Thank you, thank you, thank you and Thank you very much!" I had the same problem as Polloz. This helped.

---

### Post by PingunZ on 2005-12-30
I have the same problem here, but I cant edit the xorg.conf file
I tried to copy it to gedit and save it as etc/X11/xorg.conf but it doesnt work 
What do I have to do to change my xorg.conf file ?

Grtz PingunZ

---

### Post by kaamos on 2005-12-30
open a terminal and type
```
sudo gedit /etc/X11/xorg.conf
```

The file is outside your home directory so you must use the "sudo" command to edit it.

Whoops, thanks hamstu. fixed. :)

---

### Post by hamstu on 2005-12-30
[QUOTE=kaamos]open a terminal and type
```
sudo gedit etc/X11/xorg.conf
```

The file is outside your home directory so you must use the "sudo" command to edit it.[/QUOTE]

Don't forget the first forward slash ;)

```
sudo gedit /etc/X11/xorg.conf
```

---

