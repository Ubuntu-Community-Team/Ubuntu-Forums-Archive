---
title: "Football Manager 2015 Doesn't Work on Ubuntu 14.04"
date: 2014-12-04
forum: Gaming &amp; Leisure
---

### Post by bas4emre on 2014-12-04
Hi.


I have a problem. When i try to open Football Manager 2015, it opens a black screen on window mode during 2-3 seconds. Some outputs of necessary codes.




```
lspci | grep -E "VGA|3D|Display"
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 525M] (rev ff)

```


```
xrandr
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+   40.1  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```


```

dpkg -l | grep bumblebee
ii  bumblebee                                                   3.2.1-90~trustyppa1                                    amd64        NVIDIA Optimus support
ii  bumblebee-nvidia                                            3.2.1-90~trustyppa1                                    amd64        NVIDIA Optimus support using the proprietary NVIDIA driver

```

---

### Post by shishpt on 2015-02-06
I don't know if you resolved this issue, but I was having the same problem for a week on my Fedora setup.

I was able to get it working by running **primusrun steam **in the terminal and then click on Football Manager 2015 from the library.  

The window continued to run even after the 3 second mark and I was able to play the game.  

Hope this helps.

---

