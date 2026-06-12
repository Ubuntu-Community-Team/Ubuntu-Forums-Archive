---
title: "Monitor Resolution Change - CRT via S-video"
date: 2011-10-03
forum: Desktop Environments
---

### Post by Stoppelmonster on 2011-10-03
I am using Ubuntu 10.4 and have a VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]. I am extending my desktop via S-video to a Panasonic CT-34WX50, it is a CRT TV. I am displaying at 800x600 and would like to increase to at least 1024x768. 
I tried xrandr doing the following:

**Created a modeline with**
```
$ cvt 1024 768
```

**Modeline**
```
"1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```

**then with xrandr I created a new mode and added it**
```
$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

$ xrandr --addmode S-video 1024x768
```

I then opened the display setting GUI and selected the 1024x768 resolution for the "monitor" and applied. The monitor stopped displaying correctly, the picture was full of noise and distorted.

I tried changing back to the detected 800x600, but it wouldnt revert until restart. 

[SIZE="3"][COLOR="Red"]Any suggestion on how to change the resolution for this "monitor"? Is this an issue with the graphics card driver? Can crt monitors be used at a higher resolution than 800x600 via S-video?[/COLOR][/SIZE]

---

### Post by mcduck on 2011-10-03
No matter what resolution you set, you'll only really get the basic PAL or NTSC resolution (equivalent of 720x576 or 720x480) as S-Video is only intended for analog TV use. Setting any other resolution on your computer will simply scale that resolution into PAL/NTSC. What makes things even worse is that you'll only get interlaced scan, which practically cuts the vertical resolution in half.

If there's any chance to do so, I'd highly recommend using some connection intended for computer use instead of using S-Video.

edit: I just realized that it's a CRT *TV* you are using. In that case using a better connection would of course do nothing as the display itself is limited to the TV resolutions.

---

### Post by Stoppelmonster on 2011-10-11
Thanks, mcduck. Any chance you know how to make the CRT via S-video the default monitor for full screen from flash players in-browser. like youtube, etc...?

---

