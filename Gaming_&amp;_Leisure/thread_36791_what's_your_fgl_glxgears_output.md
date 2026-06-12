---
title: "what's your fgl_glxgears output"
date: 2005-05-24
forum: Gaming &amp; Leisure
---

### Post by Delerium on 2005-05-24
hey!

I have installed the ATI driver (fglrx) and I was wondering if my performance are acceptable:  here's the output of fgl_glxgears on a Radeon 9600XT

root@hardwired:~ # fgl_glxgears
1396 frames in 5.0 seconds = 279.200 FPS
1905 frames in 5.0 seconds = 381.000 FPS
1979 frames in 5.0 seconds = 395.800 FPS
1905 frames in 5.0 seconds = 381.000 FPS
1917 frames in 5.0 seconds = 383.400 FPS
1912 frames in 5.0 seconds = 382.400 FPS
1904 frames in 5.0 seconds = 380.800 FPS

What's yours? Thanks!

---

### Post by Ali_Baba on 2005-05-24
fgl_glxgears:

557 frames in 5.0 seconds = 111.400 FPS
474 frames in 5.0 seconds = 94.800 FPS
497 frames in 5.0 seconds = 99.400 FPS
477 frames in 5.0 seconds = 95.400 FPS
488 frames in 5.0 seconds = 97.600 FPS

ati radeon 9200 se.

I think there is nothing wrong on your drivers.

---

### Post by NoTiG on 2005-05-24
1304 frames in 5.0 seconds = 260.800 FPS
1584 frames in 5.0 seconds = 316.800 FPS
1577 frames in 5.0 seconds = 315.400 FPS
2547 frames in 5.0 seconds = 509.400 FPS
2812 frames in 5.0 seconds = 562.400 FPS
1515 frames in 5.0 seconds = 303.000 FPS
1583 frames in 5.0 seconds = 316.600 FPS
1585 frames in 5.0 seconds = 317.000 FPS
1578 frames in 5.0 seconds = 315.600 FPS
1856 frames in 5.0 seconds = 371.200 FPS
2860 frames in 5.0 seconds = 572.000 FPS
2597 frames in 5.0 seconds = 519.400 FPS

thats laptop with 9600 mobile. weird!

---

### Post by killerflo on 2005-05-25
hmmm,

bit slow

flo@ghost:~$ fgl_glxgears
969 frames in 5.0 seconds = 193.800 FPS
1318 frames in 5.0 seconds = 263.600 FPS
1293 frames in 5.0 seconds = 258.600 FPS
1309 frames in 5.0 seconds = 261.800 FPS
1332 frames in 5.0 seconds = 266.400 FPS
1367 frames in 5.0 seconds = 273.400 FPS
1365 frames in 5.0 seconds = 273.000 FPS
1365 frames in 5.0 seconds = 273.000 FPS

dont realy know what is in my laptop, it must be a mobility 9700 or 9600

---

### Post by joele on 2005-05-25
GeForce Ti 4200

15738 frames in 5.0 seconds = 3147.6 FPS

---

### Post by theerga on 2005-05-25
4155 frames in 5.0 seconds = 831.000 FPS
6885 frames in 5.0 seconds = 1377.000 FPS
6886 frames in 5.0 seconds = 1377.200 FPS
6843 frames in 5.0 seconds = 1368.600 FPS
6825 frames in 5.0 seconds = 1365.000 FPS
6830 frames in 5.0 seconds = 1366.000 FPS
6306 frames in 5.0 seconds = 1261.200 FPS
9853 frames in 5.0 seconds = 1970.600 FPS
17522 frames in 5.0 seconds = 3504.400 FPS
18006 frames in 5.0 seconds = 3601.200 FPS
18590 frames in 5.0 seconds = 3718.000 FPS
19064 frames in 5.0 seconds = 3812.800 FPS


oh yeah ownage i have a nvidia geforce fx 5200 128 mb pci 
i dont know what the jump to 3000 is about though it went back down shortly after

---

### Post by Spudgun on 2005-05-25
~7170, with a PCI Express nVidia 6600 GT :)

---

### Post by DutchLau on 2005-05-25
```
discom@discom:~$ glxgears
82804 frames in 5.0 seconds = 16560.800 FPS
82860 frames in 5.0 seconds = 16572.000 FPS
84061 frames in 5.0 seconds = 16812.200 FPS
77932 frames in 5.0 seconds = 15586.400 FPS
86221 frames in 5.0 seconds = 17244.200 FPS
78134 frames in 5.0 seconds = 15626.800 FPS
74662 frames in 5.0 seconds = 14932.400 FPS
``` 

OUCH. And that with my POS Nvidia FX 5200  :razz:

---

### Post by DutchLau on 2005-05-25
[QUOTE=killerflo]hmmm,

bit slow
[/QUOTE]


Looks like you don't have GFX drivers installed. What do you have on your desktop? An Nvidia card or a Radeon card?

---

### Post by killerflo on 2005-05-25
ok,

fgl driver is installed
__________________________

flo@ghost:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)
OpenGL extensions:
......
____________________________

it's an acer notebook pentium-m 1.4 ghz 512 mb ram and MOBILITY RADEON 9700.
don't know why it's so slow

ps fgl_gears is not glxgears

________________________

flo@ghost:~$ glxgears
6418 frames in 5.0 seconds = 1283.600 FPS
6778 frames in 5.0 seconds = 1355.600 FPS
6775 frames in 5.0 seconds = 1355.000 FPS
flo@ghost:~$ fgl_glxgears
990 frames in 5.0 seconds = 198.000 FPS
1339 frames in 5.0 seconds = 267.800 FPS
1503 frames in 5.0 seconds = 300.600 FPS
1607 frames in 5.0 seconds = 321.400 FPS
1576 frames in 5.0 seconds = 315.200 FPS
flo@ghost:~$

---

### Post by clb137 on 2005-05-25
3428 frames in 5.0 seconds = 685.600 FPS
3428 frames in 5.0 seconds = 685.600 FPS
3429 frames in 5.0 seconds = 685.800 FPS
3428 frames in 5.0 seconds = 685.600 FPS
3428 frames in 5.0 seconds = 685.600 FPS
3412 frames in 5.0 seconds = 682.400 FPS
3428 frames in 5.0 seconds = 685.600 FPS
3429 frames in 5.0 seconds = 685.800 FPS
3428 frames in 5.0 seconds = 685.600 FPS
3410 frames in 5.0 seconds = 682.000 FPS
3412 frames in 5.0 seconds = 682.400 FPS
3211 frames in 5.0 seconds = 642.200 FPS
3408 frames in 5.0 seconds = 681.600 FPS
3381 frames in 5.0 seconds = 676.200 FPS
3382 frames in 5.0 seconds = 676.400 FPS
3430 frames in 5.0 seconds = 686.000 FPS
3390 frames in 5.0 seconds = 678.000 FPS
3333 frames in 5.0 seconds = 666.600 FPS
3389 frames in 5.0 seconds = 677.800 FPS
3328 frames in 5.0 seconds = 665.600 FPS
3335 frames in 5.0 seconds = 667.000 FPS
3406 frames in 5.0 seconds = 681.200 FPS

---

### Post by clb137 on 2005-05-25
45214 frames in 5.0 seconds = 9042.800 FPS
45287 frames in 5.0 seconds = 9057.400 FPS
43164 frames in 5.0 seconds = 8632.800 FPS
31846 frames in 5.0 seconds = 6369.200 FPS
38228 frames in 5.0 seconds = 7645.600 FPS
33851 frames in 5.0 seconds = 6770.200 FPS
38523 frames in 5.0 seconds = 7704.600 FPS
32655 frames in 5.0 seconds = 6531.000 FPS
40852 frames in 5.0 seconds = 8170.400 FPS
44966 frames in 5.0 seconds = 8993.200 FPS
45655 frames in 5.0 seconds = 9131.000 FPS
45982 frames in 5.0 seconds = 9196.400 FPS
44262 frames in 5.0 seconds = 8852.400 FPS
41788 frames in 5.0 seconds = 8357.600 FPS
40650 frames in 5.0 seconds = 8130.000 FPS
43902 frames in 5.0 seconds = 8780.400 FPS
45873 frames in 5.0 seconds = 9174.600 FPS
45866 frames in 5.0 seconds = 9173.200 FPS

---

### Post by Grue on 2005-05-25
Heh, I guess this is proof that the nVIDIA drivers are somewhat more stable and optimized than the fgl drivers.

My output using a Radeon 9800 pro:

$ fgl_glxgears 
2950 frames in 5.0 seconds = 590.000 FPS
3067 frames in 5.0 seconds = 613.400 FPS
3084 frames in 5.0 seconds = 616.800 FPS

$ glxgears 
13258 frames in 5.0 seconds = 2651.600 FPS
15717 frames in 5.0 seconds = 3143.400 FPS
15089 frames in 5.0 seconds = 3017.800 FPS

I'm a bit amazed that there is such a great difference between the cards.

---

### Post by jdong on 2005-05-25
NOTE: I'm an NVIDIA fan, not an ATI fan. This statement, nonetheless, is unbiased.
 
 
Guys, glxgears is NOT a video card benchmark of any sort. Especially since you're comparing apples to oranges (two different glxgears implementations).
 
 
glxgears is only good for checking if X's GLX extension is installed properly. It's good for making sure OpenGL doesn't crash the system, and for comparing orders of magnitude (30fps vs 3000fps: the first case, 3d drivers aren't installed correctly). glxgears does **NOT** give reliable measurement of a video card's performance compared to another. Not even with repeated sampling (*). A good rule of thumb is, if you have an ATI or NVidia card and aren't getting >=1000fps with glxgears, you configured something wrong (does NOT apply to fgl_glxgears). If you have another DRI-accelerated card (like the Intel Extremes) and are not getting in the 300-1000 range, you did something wrong. Else, you're fine.
 
Use something more substantial for benchmarking, whether it's a Doom3 demo or Supertux :).
 
(*) For the statistically inclined and curious, plot 20 consecutive glxgears outputs on a histogram, then tell me if it looks remotely normal enough to warrant t/z procedures. If you're gonna argue CLS, have fun watching glxgears for 6 hours! LOL :D

---

### Post by sapo on 2005-05-25
[QUOTE=Grue]Heh, I guess this is proof that the nVIDIA drivers are somewhat more stable and optimized than the fgl drivers.

My output using a Radeon 9800 pro:

$ fgl_glxgears 
2950 frames in 5.0 seconds = 590.000 FPS
3067 frames in 5.0 seconds = 613.400 FPS
3084 frames in 5.0 seconds = 616.800 FPS

$ glxgears 
13258 frames in 5.0 seconds = 2651.600 FPS
15717 frames in 5.0 seconds = 3143.400 FPS
15089 frames in 5.0 seconds = 3017.800 FPS

I'm a bit amazed that there is such a great difference between the cards.[/QUOTE]

Same as mine

sapo@stfu:~ $ fgl_glxgears
2886 frames in 5.0 seconds = 577.200 FPS
3487 frames in 5.0 seconds = 697.400 FPS
3469 frames in 5.0 seconds = 693.800 FPS
3466 frames in 5.0 seconds = 693.200 FPS


But the truth is:

NVIDIA > ATI @ linux drivers..

I m gonna sell my 9800pro and buy a 6600GT.. almost the same price and far better  ](*,)

---

### Post by Curlydave on 2005-05-27
I've got you guys beat:

fgl_glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

---

### Post by Curlydave on 2005-05-27
Bah, I'm giving up on the new drivers. Here's the stock driver output:

david@computer:~$ fgl_glxgears
4507 frames in 5.0 seconds = 901.400 FPS
4703 frames in 5.0 seconds = 940.600 FPS
4630 frames in 5.0 seconds = 926.000 FPS
4776 frames in 5.0 seconds = 955.200 FPS
4770 frames in 5.0 seconds = 954.000 FPS
4764 frames in 5.0 seconds = 952.800 FPS
4759 frames in 5.0 seconds = 951.800 FPS

Btw, if I move my terminal window in front of the output, the framerate shoots into the thousands. Dunno why.

---

### Post by wasynyt on 2005-05-28
9914 frames in 5.0 seconds = 1982.800 FPS
10967 frames in 5.0 seconds = 2193.400 FPS
11115 frames in 5.0 seconds = 2223.000 FPS
11060 frames in 5.0 seconds = 2212.000 FPS
10825 frames in 5.0 seconds = 2165.000 FPS
9597 frames in 5.0 seconds = 1919.400 FPS
13975 frames in 5.0 seconds = 2795.000 FPS
10883 frames in 5.0 seconds = 2176.600 FPS
10992 frames in 5.0 seconds = 2198.400 FPS
10845 frames in 5.0 seconds = 2169.000 FPS

and my graphiccard is asus mx 440 128 mb (64 bit)

---

### Post by robtotheb on 2005-05-28
OK i think i win :)

55849 frames in 5.0 seconds = 11169.800 FPS
63980 frames in 5.0 seconds = 12796.000 FPS
63955 frames in 5.0 seconds = 12791.000 FPS
63977 frames in 5.0 seconds = 12795.400 FPS
63927 frames in 5.0 seconds = 12785.400 FPS

GeForce 6800 GT 256 MB  \\:D/

---

### Post by paul cooke on 2005-05-28
[QUOTE=robtotheb]OK i think i win :)

55849 frames in 5.0 seconds = 11169.800 FPS
63980 frames in 5.0 seconds = 12796.000 FPS
63955 frames in 5.0 seconds = 12791.000 FPS
63977 frames in 5.0 seconds = 12795.400 FPS
63927 frames in 5.0 seconds = 12785.400 FPS

GeForce 6800 GT 256 MB  \\:D/[/QUOTE]
 yeah... it's amazing what you get when you shrink the window or hide it...

```
paulc@big-box:~ $ glxgears
3663 frames in 5.0 seconds = 732.600 FPS
4056 frames in 5.0 seconds = 811.200 FPS
4040 frames in 5.0 seconds = 808.000 FPS
4029 frames in 5.0 seconds = 805.800 FPS
3231 frames in 5.0 seconds = 646.200 FPS
9733 frames in 5.0 seconds = 1946.600 FPS
13282 frames in 5.0 seconds = 2656.400 FPS
13324 frames in 5.0 seconds = 2664.800 FPS
13259 frames in 5.0 seconds = 2651.800 FPS
13252 frames in 5.0 seconds = 2650.400 FPS
``` 

the big jump was when I dragged the konsole window over the glxgears window...  :smile:

I think that's the end of the subject as I've just shown how fixable the output can be even with the default window.

---

### Post by robtotheb on 2005-05-28
HEY!  Im no cheat!

I get this when i hide it...

73462 frames in 5.0 seconds = 14692.400 FPS
96919 frames in 5.0 seconds = 19383.800 FPS
97775 frames in 5.0 seconds = 19555.000 FPS
97773 frames in 5.0 seconds = 19554.600 FPS
97806 frames in 5.0 seconds = 19561.200 FPS

---

### Post by toastytoast on 2008-10-17
ok for those using an nvidia card fgl_glxgears WILL GIVE YOU INCORRECT OUTPUT becasue it is made to work with the the fglrx drivers NOT THE NIVIDIA drivers but any way w/ my ati x1650 pro card i get around 1500 fps in my slackware machine w/ fgl_glxgears normal glxgears gives me about 5000 fps

---

### Post by eragon100 on 2008-10-17
> **toastytoast said:**
> ok for those using an nvidia card fgl_glxgears WILL GIVE YOU INCORRECT OUTPUT becasue it is made to work with the the fglrx drivers NOT THE NIVIDIA drivers but any way w/ my ati x1650 pro card i get around 1500 fps in my slackware machine w/ fgl_glxgears normal glxgears gives me about 5000 fps

Scary... Zombie thread!

BTW, Necromancy is cool! :)

---

### Post by chewit on 2008-10-17
200FPS - ATi Radeon 7000 PCI (64mb)

---

