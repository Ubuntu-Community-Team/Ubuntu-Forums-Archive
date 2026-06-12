---
title: "uSplash Resolution"
date: 2006-05-18
forum: Desktop Environments
---

### Post by PingunZ on 2006-05-18
I want to make my own uSplash, is there a to change the resolution of the grub splash, and the ubuntu usplash ?
My resolution is 1440*900
Can I also change the colors to 24 if possible ?

Grtz PingunZ

---

### Post by testube_babies on 2006-05-18
Unfortunately, usplash has very restricted limitations.  The image has to be 640x400 and 16 colors.  For more info, see here:
[https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

---

### Post by PingunZ on 2006-05-18
I made smething for grub ... ( view attached )
Original was a wallpaper by Anarchico
I followed[ this howto]("http://www.tldp.org/LDP/LG/current/jayanth.html")

Grtz PingunZ

---

### Post by PingunZ on 2006-05-18
Just found something in my /boot/grub/menu.lst
```
## e.g. defoptions=vga=791 resume=/dev/hda5
```

I remember some vga table so you could adjust that " 791 " to your resolution
So I looked it up and found this table 
```

                 640x480    800x600    1024x768       1280x1024
256 colors        768        771         773            775
32K colors        784        787         790            793
64K colors        785        788         791            794
16M colors        786        789         792            795

```

My resolution is 1440*900, Is there a vga mode for that too ?

Grtz PingunZ

---

### Post by PingunZ on 2006-05-18
Anybody ? :neutral:

---

### Post by elamericano on 2006-05-18
No, but your video card should support a standard resolution at boot time.

The closest I could find is:
1400x1050
16 bit = 834
24 bit = 835

I doubt these will work for you. I would try 791-799 to see what gives you the best results.

---

### Post by mlind on 2006-05-18
Linux kernel documentation will aid you a bit

/usr/src/linux/Documentation/svga.txt
/usr/src/linux/Documentation/fb/vesafb.txt

if you haven't installed 'linux-source' -package, you can find contents of these files
using google.

you can find out supported modes by inserting **vga=ask** to /boot/grub/menu.lst
```

# defoptions=**vga=ask** nosplash

```

then run *sudo update-grub* and boot. At boottime grub will display valid
modes for frame buffer.

---

### Post by mlind on 2006-05-18
if you need to convert values from hex to decimal format use

```

printf "%d\n" *hex_value*

```

for example, to find out decimal equivalent for mode 0x317
```

printf "%d\n" 0x317

```
will output value: 791

---

### Post by elamericano on 2006-05-18
BTW, this might improve your display slightly, but it does not overcome the limitation of usplash. You may want to try splashy:

[http://splashy.alioth.debian.org/wiki/doku.php?id=installation](http://splashy.alioth.debian.org/wiki/doku.php?id=installation)
[http://ubuntuforums.org/showthread.php?t=41709](http://ubuntuforums.org/showthread.php?t=41709)

---

### Post by j_baer on 2006-05-22
[QUOTE=PingunZ]I want to make my own uSplash, is there a to change the resolution of the grub splash, and the ubuntu usplash ?
My resolution is 1440*900
Can I also change the colors to 24 if possible ?

Grtz PingunZ[/QUOTE]

See link ...

[http://www.ubuntuforums.org/showthread.php?t=180393](http://www.ubuntuforums.org/showthread.php?t=180393)

---

### Post by PingunZ on 2006-05-31
Yeah so wat should I see on that link j_baer ? I'm wondering if there is one for 1440*900 .. I can't find anthing of that in that thread.

Grtz PingunZ

---

