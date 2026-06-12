---
title: "xrandr custom resolution"
date: 2009-05-21
forum: General Help
---

### Post by haris.bogdanovic on 2009-05-21
Hi.

I would like to have a 960x600@60 resolution on my Ubuntu 9.04, Fujistu-Siemens Esprimo v5535 with sis mirage 3 video card.
Is that possible on my video card and how to add custom resolutions in general (with xrandr or some other way) ?
Where have all configuration lines from xorg.conf gone in 9.04 ?
I could set resolutions in xorg.conf but I think that's not the way in 9.04.
How would <modeline> parameter have to look for 960x600@60 ?

Thanks
Haris

---

### Post by CatKiller on 2009-05-21
Isn't 1280×800 the native resolution for that screen? It's likely to look bad at a non-native resolution.

> **haris.bogdanovic said:**
> How would <modeline> parameter have to look for 960x600@60 ?

Modeline "960x600@60"       45.28   960  992 1160 1192    600  612  618  631

according to [this page]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl").

---

### Post by blackened on 2009-05-21
> **CatKiller said:**
> Isn't 1280×800 the native resolution for that screen? It's likely to look bad at a non-native resolution...

That resolution is of the same aspect ratio, so it shouldn't look too bad.

First you'll need to generate a modeline for that resolution:

```
gtf 960 600 60
```

which should output something like

```
  # 960x600 @ 60.00 Hz (GTF) hsync: 37.32 kHz; pclk: 45.98 MHz
  Modeline **"960x600_60.00"  45.98  960 1000 1096 1232  600 601 604 622  -HSync +Vsync**
```

then create a new resolution mode that uses that modeline (the part in bold, yours might be different so make sure you run the gtf command first):

```
xrandr --newmode "960x600_60.00"  45.98  960 1000 1096 1232  600 601 604 622  -HSync +Vsync
``` 

now attach the new mode to the appropriate interface:

```
xrandr --addmode LVDS 960x600_60.00
```

then switch to it using

```
xrandr --output LVDS --mode 960x600_60.00
```


You can script all your resolution changes depending on the active interface, but that's a little beyond the scope of the question. Here is a page with some info on persistence in xrandr changes: [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution").

Good luck

---

### Post by haris.bogdanovic on 2009-05-21
I got this output:

xrandr: Configure crtc 0 failed

I can only set 640x480 and 800x600 which where available after Ubuntu install.
In Windows XP I can set 640x480, 800x600, 1024x768 and 1280x800 with original driver and with default Microsoft driver  1280x768 added to original resolutrions.
I tried get-edid but nothing came up.
I also tried to add my 800x600 resolution from gtf result but Ubuntu switched to default 800x600 which it set after install.
For any custom resolution I get the same message.

This is what I get with xrandr --verbose:

  800x600 (0x102)   29.3MHz *current
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.6KHz
        v: height  600 start    0 end    0 total  600           clock   61.0Hz
  640x480 (0x103)   18.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   28.8KHz
        v: height  480 start    0 end    0 total  480           clock   60.0Hz

  960x600 (0x11d)   46.0MHz -HSync +VSync
        h: width   960 start 1000 end 1096 total 1232 skew    0 clock   37.3KHz
        v: height  600 start  601 end  604 total  622           clock   60.0Hz

First two resolutions were created by Ubuntu, and third by me.
Can I get zeros at start and end columns because I noticed that every resolution I create has some number for start and end and they do not work. Those two which have zeros for start and end work.

I don't have LVDS output, only "default" output.

---

### Post by CatKiller on 2009-05-21
> **blackened said:**
> That resolution is of the same aspect ratio, so it shouldn't look too bad.

It's not really a question of aspect ratio with an LCD. The pixel size is fixed in an LCD screen, so if you run a non-native resolution the pixels in your image don't line up with the pixels in the screen, and everything ends up looking blurry and rubbish. It's true that if the aspect ration was wrong too it would look even worse, but it's bad enough just running non-native.

To the OP:

Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by blackened on 2009-05-22
> **CatKiller said:**
> It's not really a question of aspect ratio with an LCD. The pixel size is fixed in an LCD screen, so if you run a non-native resolution the pixels in your image don't line up with the pixels in the screen, and everything ends up looking blurry and rubbish...

Guess I never really thought of it that way, but it makes sense. Thanks for the info.

I'll bet that would wreak sheer hell on subpixel font rendering as well.

---

### Post by haris.bogdanovic on 2009-05-22
The only reason I would like to have 960x600 reslution is because I hjave a 16:10 screen and the only resolution that's available is 1280x800, that is to small for me.
I can increase dpi but web pages don't look as they should and I'd like to make web content.
Any 16:10 resolution around 960x600 would be fine.
I guess I will have to learn to calculate modeline by hand because obviously calculators on some web pages don't give me correct results, as well as gtf in command line.
 
And changing xorg.conf is, I guess, not the way in 9.04 because it is practically empty on install.
By the way, where are all configuration options gone from xorg.conf in 9.04 ?

---

### Post by CatKiller on 2009-05-22
> **haris.bogdanovic said:**
> I can increase dpi but **already broken** web pages don't look as they should

T;FTFY :)

Good web designers know that their users will be viewing the site at any number of resolutions and make their sites scale accordingly. People don't all use 640×480 any more.

If the writing's small for you, increase the font size. It's easy enough to do it for the whole system. You'll have a much better experience than running your monitor in blurry mode.

---

### Post by haris.bogdanovic on 2009-05-22
Nobody said that 960x600 or any other smaller 16:10 resolution is blurry.
I didn't succeed to display any of these resolutionso I don't know how they look.
I was calculatinfg how many pixels could my monitor display:
Lowest common deominator of 640, 800 and 1280 is 6400 and 6400/960 is not a whole number so I guess 960x600 would be blurry but there are other smaller 16:10 resolutions and I didn'T even get 800x600 to work (with modeline that calculator on web or gtf created) so as I said I will have to learn to calculate modeline by hand to get even 800x600 to work.
I know that users see web pages at many resolutions but they all use 96 dpi, standard font size and resolution which has the same aspect ratio as monitor.

---

### Post by CatKiller on 2009-05-22
> **haris.bogdanovic said:**
> Nobody said that 960x600 or any other smaller 16:10 resolution is blurry.

I did. A non-native resolution on an LCD monitor **will** be blurry. Actually, I tell a lie; 640×400 & 320×200 would probably be fine. Maybe it wouldn't be a problem for you, but it would definitely drive me nuts.

> I know that users see web pages at many resolutions but they all use 96 dpi, standard font size and resolution which has the same aspect ratio as monitor.

Sure, the resolution would have the same aspect ratio as the monitor. Anything else would just be crazy.

But they certainly don't all use the same font size or DPI. There are over a billion Internet users in the world using all sorts of devices to connect, including netbooks and mobile phones. You need to broaden your horizons when it comes to web development.

---

### Post by haris.bogdanovic on 2009-05-22
How about:
 
384x240
480x300
512x320
768x480
960x600
1024x640
 
How do you know how many real pixels has my monitor got in horizontal and vertical ?

---

### Post by CatKiller on 2009-05-23
> **haris.bogdanovic said:**
> How do you know how many real pixels has my monitor got in horizontal and vertical ?

The manual gives the native resolution for that screen. It's 1280×800.

---

### Post by mushis on 2010-02-11
Hi,

Ive followed all the procedures to create my custom resolution of 800x600 @ 154hz

but when i enter the command to change the mode to the new one:
xrandr --output default --mode 800x600_154

I get this output error:
xrandr: Configure crtc 0 failed


Please help. Ive searched for hours in google without any luck. Anyone knows what causes this error and how i can fix it?
Thanks in advance!


edit: would it be related to having my output name "default" instead of "vga" or other less generic term?
I forgot to mention i sucesfully made a modeLine for 1600x1200@76hz. And that i tried other hz for 800x600, without success (same error)

---

### Post by FA5878 on 2010-03-24
Hi, one of my laptops is an Esprimo v5355 and I have been having difficulties getting the screen resolution set to its native settings of 1280x800, it will not let me go greater than 800x600

I followed the instructions above and eventually hit this dead end:
```
:~$ xrandr --output default --mode 1280x800_75.00
xrandr: screen cannot be larger than 800x600 (desired size 1280x800)
```

Any suggestions to what I am doing wrong please?

---

### Post by venkivoice on 2010-03-26
try this in your 45custom_xrandr file.

Replace the below content to your 45custome_xrandr and do take a backup of your present xrandr settings.


display=`xrandr | grep " connected " |awk ' {print $1}'`
#echo $display

str=`xrandr | grep "1920x1080_60.00" |awk ' {print $1}'`
#echo $str

if [ ! -n "$str" ]; then
    #echo "inif"
    xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    xrandr --addmode $display 1920x1080_60.00
    xrandr --output $display --mode 1920x1080_60.00
else
    #echo "inelse"
    xrandr --output $display --mode 1920x1080_60.00
fi


Hope it will help you. 

Thanks & regards,
Venkat
> **FA5878 said:**
> Hi, one of my laptops is an Esprimo v5355 and I have been having difficulties getting the screen resolution set to its native settings of 1280x800, it will not let me go greater than 800x600

I followed the instructions above and eventually hit this dead end:
```
:~$ xrandr --output default --mode 1280x800_75.00
xrandr: screen cannot be larger than 800x600 (desired size 1280x800)
```Any suggestions to what I am doing wrong please?

---

### Post by venkivoice on 2010-03-26
Hi There,

Sorry I made a mistake in the reply.

Please use the below one. In the previous post i posted it for 1920*1080.. Sory ;)

display=`xrandr | grep " connected " |awk ' {print $1}'`
#echo $display

str=`xrandr | grep "1280x800_60.00" |awk ' {print $1}'`
#echo $str

if [ ! -n "$str" ]; then
    #echo "inif"
    xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
    xrandr --addmode $display 1280x800_60.00
    xrandr --output $display --mode 1280x800_60.00
else
    #echo "inelse"
    xrandr --output $display --mode 1280x800_60.00
fi

> **venkivoice said:**
> try this in your 45custom_xrandr file.

Replace the below content to your 45custome_xrandr and do take a backup of your present xrandr settings.


display=`xrandr | grep " connected " |awk ' {print $1}'`
#echo $display

str=`xrandr | grep "1920x1080_60.00" |awk ' {print $1}'`
#echo $str

if [ ! -n "$str" ]; then
    #echo "inif"
    xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    xrandr --addmode $display 1920x1080_60.00
    xrandr --output $display --mode 1920x1080_60.00
else
    #echo "inelse"
    xrandr --output $display --mode 1920x1080_60.00
fi


Hope it will help you. 

Thanks & regards,
Venkat

---

