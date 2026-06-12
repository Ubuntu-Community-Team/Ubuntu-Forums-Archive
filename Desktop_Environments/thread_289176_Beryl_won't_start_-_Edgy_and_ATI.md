---
title: "Beryl won't start - Edgy and ATI"
date: 2006-10-30
forum: Desktop Environments
---

### Post by gagge on 2006-10-30
Hi,

I'm pretty new with Ubuntu.
Tried installing Beryl, but it won't start.
I used this guide to install: [http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
I have a ATI Radeon X800XT graphics card.

I don't get any errors when starting beryl, 'beryl' and 'beryl-manager' executes, but every window loses it's border.
I can see the Beryl icon in the traybar, but I can't click it, I can't click on anything actually, have to restart X.

---

### Post by noomz on 2006-10-30
I use this: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
But have a problem too.

```
glxinfo|grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9550 Generic
```

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6065 (8.29.6)
```

When I started XGL session there's no decoration..
and No direct rendering too.

---

### Post by blitzer on 2006-10-30
Beryl is very "Alpha" application and seems to work on very few systems including mine.  I have read so many post including beryl forums stating - Aiglx, Xgl, DRI, Fglrx and extensions How - To's to no avail :confused: 

The people who say they have it running and running well usually don't have their system specs listed to let us see how different computer systems are ](*,)   If they are using Edgy included ATI driver, ATI driver from ATI or opensourced driver ?

I hope this is sorted out in some logical manner in the near future -  This will be a great feature to gather the masses to Ubuntu - Linux :rolleyes: 

I had beryl running (very limited) on dapper and will not run on Edgy :-k

```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
```

```
$ glxinfo|grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
```

---

### Post by blitzer on 2006-10-30
As I am writing this post in the wonderful world of Beryl desktop :D  so I hope you will to after following this [TERRIFIC GUI HOW TO 8) ]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")

I thank you very much [COLOR="Red"]Lennart Hansen[/COLOR] ;) for this graphical how to.


It did crash the first time I rebooted but ran smoothly the next reboot which  I am typing this post.

Please post back to let us know if all is good in beryl land ;)

---

