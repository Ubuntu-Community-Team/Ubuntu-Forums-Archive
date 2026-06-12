---
title: "Screen Resolution - x server does not support the xrandr"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by gators38 on 2008-04-15
I get the following error when I go to Screen Resolution settings:
The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

Should I just add the resolution options I want in the xorg file?

---

### Post by Zorael on 2008-04-15
At least for Nvidia cards, you need to enable randr support in your /etc/X11/xorg.conf file. Whether it's supposed to be under the Screen or the videocard Device section I can't say, though.

```
	Option "RandRRotation" "true"
```

---

### Post by gators38 on 2008-04-16
I have a radeon x1600. I still get the error message.

---

### Post by Zorael on 2008-04-16
Googling around I found this example.
```
Section "Device"
        Identifier      "ati0"
        Driver          "ati"
        BusID           "PCI:4:0:0"
        Screen          0
        Option "RandRRotation" "on"
        Option "RandR" "on"
        Option "DRI" "off"
EndSection

Section "Screen"
        Identifier      "screen0"
        Device          "ati0"
        Monitor         "monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
        Option         "Rotate" "left"
[b]        Option "RandRRotation" "on"
        Option "RandR" "on"[/b]
EndSection
```

Perhaps it should be "on" for both Nvidia and ATI cards, and RandR instead of RandRRotation for ATI cards?

---

### Post by bazaloo on 2008-04-26
Try rebuilding the xorg.conf file:

sudo dpkg-reconfigure xserver-xorg

Then restart the machine. That worked for me :)

---

### Post by coogs08 on 2008-04-30
I'm using a Hp Pavilion dv6000 with an nvidia video card and Ubuntu 8.04 and I have the same problem.  I tryied editing the options in the xorg file and I tried rebuilding thet xorg file.  The former resulted in no apparent change and the latter solved the issue but compiz-fusion seemed to no longer work.  Also, after rebuilding the xorg file the windows had trails when you moved them and the image behind the windows when you moved them took a second to render.

I hope that makes sense.  I'm relatively new to Linux.

---

### Post by elustran on 2008-05-05
I'm having this problem too... and rebuilding xorg totally messed things up.  For whatever reason, it killed all of my screen and driver settings and never once prompted me for settings information

Now I'm restoring from the backup, but I'm still not sure what to do.

---

### Post by Viitala on 2008-05-06
Sucks, I have the same problem too and I tried both!

---

### Post by gmoctav on 2008-05-14
> **Viitala said:**
> Sucks, I have the same problem too and I tried both!

ME TOO. i'm using an ATI x550 on a hardy upgrade from gutsy,and i had serious problems with the monitor after modifying xorg.conf the way it was sugestted (in the device and screen sections)

---

### Post by evw2k on 2008-05-14
ati radeon 1600 same problem. started just as i updated from gutsy to whatever the 'h' one is

---

### Post by revolutio on 2008-05-16
Not being able to change my resolution and rotate my monitor with any degree of ease is a tad annoying.  Any ideas on fixing this?

---

### Post by ram130 on 2008-05-19
Im having this problem also....im on a nvidia card..ANYONE CAN HELP????

---

### Post by fantasyl on 2008-05-20
The rotation option under system->preferences->screen resolution was disabled for me, too, but it was really easy to solve (at least with my nvidia 8600GT).

Run in terminal:
```

sudo gedit /etc/X11/xorg.conf

```

and, as Zorael said, add to your xorg.conf ("Device" section)
```
Option "RandRRotation" "on"
Option "RandR" "on"

```

Restart gnome (ctrl+alt+bkspace) and go to system->preferences->screen resolution to find the rotation option enabled; that worked flawlessy for me.
After pivoting I enabled the extra visual effects ...WOW, now compiz works in portrait 1200x1920 mode, too!

PS Check that you're using the restricted nvidia driver, for the RandR extension to work....

---

### Post by ibharathy on 2008-05-29
Same error

" The X Server does not support the XRandR extension.
Runtime resolution changes to the display size are not available"

This happened after upgrading it from Gutsy to Hardy heron..

I am using AMD Processor and ASUS mother board....

---

### Post by BlackholeZ on 2008-06-04
I'm also having the same issue on my HP dv8000 with ATI video using  fglrx drivers on 8.04. Through my searching trying to get compiz to work i installed xserver-xgl. I can get things working sort of, but I'm stuck at a ridiculously low resolution and get the "x server does not support..."

I've read that things may not work 100% on machines that have updated from earlier versions. As 7.04 was originally installed on this laptop, my next step will be to try a fresh install of 8.04

I've been searching for about a week on this issue, if I missed anything, I would appreciate any suggestions, I am pretty new to linux.

-Dan

---

