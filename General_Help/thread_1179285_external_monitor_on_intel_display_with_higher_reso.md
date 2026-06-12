---
title: "external monitor on intel display with higher resolution"
date: 2009-06-05
forum: General Help
---

### Post by joetsuihk on 2009-06-05
ok, i have searched google and this forum, but my situation is a little bit different from some well known search results.

i am on a netbook actually, acer aspire one, with an intel display card.(1024x600 LCD)

actually, i can extended my desktop to my 23' Mon, but with only 1024x768. but the MON is actually 1920x1080. the System->Preference->display do not have an option of that resolution.

it can be done on WINXP, so i think it may not be a vram problem?

Joe

---

### Post by Legace on 2009-06-05
Post contents of **/etc/X11/xorg.conf**

---

### Post by joetsuihk on 2009-06-05
thanks!!

##################################
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1024 1368
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by Legace on 2009-06-05
1) Plug in your external monitor
2) Open Terminal
3) Enter the following code and post output here:
```
xrandr
```

---

### Post by joetsuihk on 2009-06-05
thanks!

FYI, i am already connected the external monitor with 1024x768 screen.... on a 23' Mon with 1920x1080

################################
Screen 0: minimum 320 x 200, current 1024 x 1368, maximum 1024 x 1368
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
LVDS connected 1024x600+0+768 (normal left inverted right x axis y axis) 222mm x 125mm
   1024x600       60.0*+
   800x600        60.3  
   640x480        59.9

---

### Post by Legace on 2009-06-05
What is a mon? Monitor?
And have you connected your external monitor via the VGA plug?

---

### Post by joetsuihk on 2009-06-05
sorry, yes, Monitor.

that is some short terms in my culture around. i mean, yes, 23' Monitor

---

### Post by Legace on 2009-06-05
Have you connected your external monitor via the VGA plug?
And could you me the refresh rate of your external monitor? If you don't know what I'm talking about, post the model of your monitor :)

---

### Post by joetsuihk on 2009-06-05
yes, via VGA.
the desktop had already extended, but not in a optimized resolution.

it is now 60Hz, as the Display settings in ubuntu is 60Hz.(there is only one option-60Hz)

---

### Post by Legace on 2009-06-05
Open Terminal.
Type in:
```
xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
```

Then type in:
```
xrandr --addmode VGA 1920x1080
```

Now type in:
```
xrandr --output VGA --mode 1920x1080
```

---

### Post by joetsuihk on 2009-06-05
i will try it, but can you explain more on what they actually do?

as i have more than 1 external Monitor (home and @work)

---

### Post by joetsuihk on 2009-06-05
on last command, it returns:
> xrandr: screen cannot be larger than 1024x1368 (desired size 1920x1368)


and i think the second and third line should use 1920x1080_60.00 instead of 1920x1080 ?

---

### Post by Legace on 2009-06-05
Create a new mode with 1920x1080 resolution at 60Hz.
```
xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
```

Add the newly created mode to the VGA output.
```
xrandr --addmode VGA 1920x1080
```

The following tells Ubuntu to use the 1920x1080 resolution.
```
xrandr --output VGA --mode 1920x1080
```

---

### Post by Legace on 2009-06-05
> **joetsuihk said:**
> and i think the second and third line should use 1920x1080_60.00 instead of 1920x1080 ?

You could try..

If that doesn't work, type in:
```
sudo gedit /etc/X11/xorg.conf
```

and comment the virtual line out.
Like this:
```
#Virtual 1024 1368
```

---

### Post by joetsuihk on 2009-06-05
strange...

i can set to 1650x1080 @60 Hz in "Display" now(great thanks!), but not a option for 1920x1080, any idea?

i should try the commands (1st one?) again?

###################
#xrandr
###################
Screen 0: minimum 320 x 200, current 1680 x 1650, maximum 1920 x 1680
VGA connected 1680x1050+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1680x1050      60.0* 
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
LVDS connected 1024x600+656+1050 (normal left inverted right x axis y axis) 222mm x 125mm
   1024x600       60.0*+
   800x600        60.3  
   640x480        59.9

---

### Post by Legace on 2009-06-05
double post, ignore

---

### Post by Legace on 2009-06-05
Try this now:

```
xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
xrandr --addmode VGA 1920x1080
xrandr --output VGA --mode 1920x1080
```

---

### Post by joetsuihk on 2009-06-05
it works!

but if you dont mind, can you explain what is hsync-start hsync-end and htotal?

clock MHz is a calculated value?

---

### Post by Legace on 2009-06-05
Glad it works :)

You can calculate those with the gtf tool in Terminal.

For example (X, Y, refresh rate):
```
gtf 1920 1080 60
```

---

### Post by joetsuihk on 2009-06-05
it just works!

thank you so much!

last hint for late comers:

> xrandr: screen cannot be larger than XXXXXXXXXXX

you may try to set it from "Display" under System->Preference
then, logout and login!

---

### Post by ThomasGHenry on 2009-06-10
Heya, 

 I'm having a similar issue. I'm connected via VGA from a Thinkpad T60 running Ubuntu 8.10 (Intrepid Ibex, if you're nasty) to a 23" LG W2361V LCD monitor with 1920 x 1080 resolution and 60 Hz refresh rate.

Here's my info:


/etc/X11/xorg.conf
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```



```
 
$  xrandr

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 2960 x 1050
VGA-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1680x1050      60.0*    60.0  
   1600x1024      60.2  
   1400x1050      70.0     60.0  
   1280x1024      75.0     75.0     60.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     60.0     59.9  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1400x1050      60.0 +   50.0  
   1280x1024      60.0     60.0  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0     59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
  1920x1080_60.00 (0x89)  172.8MHz
        h: width  1920 start 2040 end 2248 total 2576 skew    0 clock   67.1KHz
        v: height 1080 start 1081 end 1084 total 1118           clock   60.0Hz

```
 

```


$  gtf 1920 1080 60 -v


 1: [H PIXELS RND]             :     1920.000000
 2: [V LINES RND]              :     1080.000000
 3: [V FIELD RATE RQD]         :       60.000000
 4: [TOP MARGIN (LINES)]       :        0.000000
 5: [BOT MARGIN (LINES)]       :        0.000000
 6: [INTERLACE]                :        0.000000
 7: [H PERIOD EST]             :       14.909035
 8: [V SYNC+BP]                :       37.000000
 9: [V BACK PORCH]             :       34.000000
10: [TOTAL V LINES]            :     1118.000000
11: [V FIELD RATE EST]         :       59.994118
12: [H PERIOD]                 :       14.907573
13: [V FIELD RATE]             :       60.000000
14: [V FRAME RATE]             :       60.000000
15: [LEFT MARGIN (PIXELS)]     :        0.000000
16: [RIGHT MARGIN (PIXELS)]    :        0.000000
17: [TOTAL ACTIVE PIXELS]      :     1920.000000
18: [IDEAL DUTY CYCLE]         :       25.527727
19: [H BLANK (PIXELS)]         :      656.000000
20: [TOTAL PIXELS]             :     2576.000000
21: [PIXEL FREQ]               :      172.798083
22: [H FREQ]                   :       67.080001
17: [H SYNC (PIXELS)]          :      208.000000
18: [H FRONT PORCH (PIXELS)]   :      120.000000
36: [V ODD FRONT PORCH(LINES)] :        1.000000

  # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync


```


here we go........

```

$  xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync


X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  16 ()
  Serial number of failed request:  16
  Current serial number in output stream:  16


```

and there is ends...  I'll be googling meanwhile.. but I figured this conversation was fresh enough to try.

Thanks!

---

### Post by hazelnusse on 2009-06-14
I have a Dell E1505 with a ATI Mobility X1400 adapter and want to get the external monitor resolution to be the native one of my Dell 24" LCD -- 1920x1200.  When I follow the commands you suggested, I get:
```

root@DELL-E1505:/home/luke# xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
No protocol specified
Can't open display :0.0

```Here is the contents of my xorg.conf:
```

Section "ServerFlags"
        Option  "DontZap"       "True"
EndSection

```I am running Kubuntu 9.04, and when I go to the display system settings, it recognizes my laptop screen as LVDS and has lots of modes (including the native laptop resolution), but under the VGA, it has lots of modes (but not the native 1920x1200).  Where is this information stored, and why do some people have it in their xorg.conf and in my case, it isn't stored there?

Also, what does this mean:
```

root@DELL-E1505:/etc/X11# xrandr
No protocol specified
Can't open display :0.0

```Can anybody help me out so I can get my external display resolutions set?

Thanks,
~Luke

---

### Post by ThomasGHenry on 2009-06-14
What worked for me in the end was booting to my XP partition later that day, setting up the monitor there, then trying ubuntu again. It wasn't my intention to have that be a solution (and I'm not certain that was the cause), but after that everything worked as expected. 

maybe that will demystify something for someone.

---

### Post by elasticrock on 2009-08-17
This worked for me in setting my ViewSonic monitor to 1680x1050; I used gtf to find the right numbers to put in. 

> **Legace said:**
> Try this now:

```
xrandr --newmode "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
xrandr --addmode VGA 1920x1080
xrandr --output VGA --mode 1920x1080
```

I was wondering if there was a way to permanently add the new mode to the available modes in Display Preferences (System->Preferences->Display)? For now, I have a script that just runs the appropriate xrandr commands (I need to run these every time I log in). I would like to be able to have the resolution automatically detected and able to be selected from the Display Preferences drop-down box.

Thanks in advance.

---

