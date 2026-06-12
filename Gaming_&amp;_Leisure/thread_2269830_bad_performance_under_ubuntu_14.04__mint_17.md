---
title: "bad performance under ubuntu 14.04 / mint 17"
date: 2015-03-18
forum: Gaming &amp; Leisure
---

### Post by jdissl on 2015-03-18
Hello,

i have very bad performance under ubuntu or mint. im trying 3 games.
my system:

Asus P8P67 REV. 1.0
Intel Core i5-2500@3,3ghz
Sapphire ATI HD6850 1GB
Asus Xonar DG
8GB Ram

1. Counter-Strike Global offensive: 50 - 120 fps under windows 120 - 270 fps
2. Cities Skyline 10 fps under windows 30-40 fps
3. Metro 2033 i dont see the fps but the game run very bad under linux


i testing the driver from the amd website and the includet fglrx driver. makes no difference.

the pc is playing very quietly under linux in. I think the hardware is simply not used properly.

sry for bad english

[[IMG]http://fs2.directupload.net/images/150318/temp/8xgvl6km.png[/IMG]]("http://www.directupload.net/file/d/3930/8xgvl6km_png.htm")

[TABLE="class: ls2"]
[TR]
[TH][/TH]
[/TR]
[TR]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by R33D3M33R on 2015-03-18
If proprietary drivers are properly installed, you should see something like this when opening the CCC (please note that this is an old screenshot):

 [ATTACH=CONFIG]260715[/ATTACH]

If this isn't the case, then the drivers are not correctly installed. See [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) for installation instructions.

---

### Post by jdissl on 2015-03-19
everything looks good

[[IMG]http://fs2.directupload.net/images/150319/temp/lavtywrl.jpg[/IMG]](http://www.directupload.net/file/d/3931/lavtywrl_jpg.htm)

---

### Post by mastablasta on 2015-03-19
is everything propperly initialised? all libraries installed? [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

QIII blogged about R9 series and how you need to initialise it properly to get the full power. I think he added some libraries maybe?: [http://theleftcoastgeek.net/](http://theleftcoastgeek.net/)

and these 6xxx chips use similar architecture.

also can your eye actually see the difference between 60 FPS and 100 FPS? :P

anyway while fglrx is working worse than in windows it should be such a performance drop. What is your kernel? I read there are some issues with certain kernels in HWE stack. it doesn't get a good install or something. edit: here is is: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)

---

### Post by jdissl on 2015-03-19
many thanks.

I install Ubuntu this weekend new and install the driver to install according to the instructions. I 've tried around a lot in the last few weeks . I would like to try a fresh installation again.


normaly i cant see a different between 60 and 100 fps but cs go feels lagy with 60 fps. and in cs go , you should have at least the same fps as tick of the server. otherwise it lags for the other players.

---

### Post by mastablasta on 2015-03-20
well just found this for another thread: [http://www.phoronix.com/scan.php?page=article&item=valve_20amd_gpus&num=1](http://www.phoronix.com/scan.php?page=article&item=valve_20amd_gpus&num=1)

if it works with opensource drivers well then it should with proprietary even better.

the FPS was kind of a joke. as human eye is not capable to distinguish these. and then there is the monitor refresh rate etc. anyway I hope you find the sweet spot you want.

---

### Post by R33D3M33R on 2015-03-20
If the FPS fluctuates you will see stuttering. Since the driver is ok, I would recommend lowering settings/resolution and if this doesn't work, give the opensource driver a try. So: don't install fglrx on your new Ubuntu install, just try to run the games ...

---

### Post by jdissl on 2015-03-20
so, i installed ubuntu 14.04 and steam new. steam installed then mesa. cities runs with 37 fps. and cs go with 60.

i think in mesa is vsync activated. how i can disable this?

thank you very much for help

---

### Post by R33D3M33R on 2015-03-20
Create a file named .drirc in your home directory (it will be hidden since it has a dot in front of it).

Put this in:

```

<driconf>
    <device screen="0" driver="dri2">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
    <!-- Other devices ... -->
</driconf>
```

If you want to see FPS on screen, run the game with:

```
GALLIUM_HUD=fps game_executable
```

In Steam enter this in launch options:

```
GALLIUM_HUD=fps %command%
```

---

### Post by jdissl on 2015-03-20
it works in cities skyline and glxgears, but in cs go and tf2 not. ingame was the vsync disabled

---

### Post by R33D3M33R on 2015-03-23
Try something of this then: [http://stackoverflow.com/questions/17196117/disable-vertical-sync-for-glxgears](http://stackoverflow.com/questions/17196117/disable-vertical-sync-for-glxgears)

---

### Post by jdissl on 2015-04-08
sorry for the long break but unfortunately I did not have time. but now i had time.

it works with the xorg.conf modification. the fps are lower as in windows, but it runs smooth. i will testing it the next days


thanks a lot for your help

---

