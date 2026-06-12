---
title: "xrandr transform help"
date: 2018-02-26
forum: Desktop Environments
---

### Post by jowilliamson on 2018-02-26
I have a projector which is fixed in a position too close to the screen so the image is too large. Yes I know, buy a new projector.....

Anyway, using Kodi calibration options I am able to easily adjust the position and size of the screen without too much quality loss. 


```
<description>Projector</description>
            <subtitles>919</subtitles>
            <pixelratio>1.000000</pixelratio>
            <refreshrate>30.000000</refreshrate>
            <output>HDMI-2</output>
            <xrandrid>0x46</xrandrid>
            <overscan>
                <left>121</left>
                <top>21</top>
                <right>1865</right>
                <bottom>1004</bottom>
            </overscan>
...

```

I notice here there is an xrandrid, does this mean I can use this directly to achieve the same with xrandr so the whole ubuntu desktop is adjusted to fit? 

If not, what would achieve the same using xrandr? So far I think I have nailed the left and top settings but not sure if I need to combine with scale or which of these number represent bottom and right if I can do the whole thing in transform:
```

xrandr --output HDMI-1 --mode 1920x1080  --transform 1,0,-121,0,1,-21,0,0,1

```

Many thanks in advance to all those who don't tell me to physically move the projector :P

---

