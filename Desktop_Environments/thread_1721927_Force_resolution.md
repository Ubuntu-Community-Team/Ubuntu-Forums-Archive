---
title: "Force resolution"
date: 2011-04-05
forum: Desktop Environments
---

### Post by ryezs on 2011-04-05
Hi
When i start my computer without the screen and then plug it in after boot the resolution is wrong, it becomes 1440x1050 (4:3) and the screen's native is 1920x1080. This is a problem cause i need to start it without the screen and then plug it in. i have tried some stuff that i found on the forums but nothing helped. I'm using Ubuntu 10.04, AMD 4350 and fglrx drivers.

I tried to add this to Section "Screen" in xorg.conf
```
 
SubSection     "Display"
        Depth       24
        Modes      "1920x1080"
EndSubSection

```
and this to Section Monitor
```
 
Option "noDDC"

```

but nothing seem to work the resolution is still 1440x1050. If i run xrandr the highest resolution is 1440x1050 and i have tried to add a new mode with
```

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DFP2 1920x1080

```
When it has booted up without the screen it still says that it is connected with DFP2 1920x1080 and the highest resolution is 1440x1050.
xrandr output
```

Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       75.0     60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x480        60.0  
   640x480        75.0     60.0  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0xc1)  148.5MHz
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz

```

my xorg.conf
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "1920x1080"
	EndSubSection
EndSection

#Section "Monitor"
#        Identifier      "Configured Monitor"
#        Vendorname      "Generic LCD Display"
#        Modelname       "LCD Panel 1920x1080"
#        Horizsync       31.5-74.5
#        Vertrefresh     59.9 - 60.1
#        Modeline 	"1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
#        Gamma   1.0
#EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
	Option "NoDDC"
EndSection

Section "ServerFlags"
	Option "blank time"  "0"
	Option "standby time" "0"
	Option "suspnd time" "0"
	Option "off time" "0"
EndSection
```

---

### Post by Krytarik on 2011-04-05
> **ryezs said:**
> 
```

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DFP2 1920x1080

```
After running those commands, you need also to apply the added mode to the output, like this:
```
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DFP2 1920x1080_60.00
xrandr --output DFP2 --mode 1920x1080_60.00

```Try setting the mode by running those commands in a terminal, if that works, you need to make them run at startup, I recommend to do so by adding them to the startup script of GDM, all that is described in this guide:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Greetings.

---

### Post by ryezs on 2011-04-06
> **Krytarik said:**
> After running those commands, you need also to apply the added mode to the output, like this:
```
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DFP2 1920x1080_60.00
xrandr --output DFP2 --mode 1920x1080_60.00

```
Thanks for the answer i have read the link you posted but i still have some problems. If a set "xrandr --output DFP2 --mode 1920x1080_60.00" i get ```
xrandr: screen cannot be larger than 1600x1600 (desired size 1920x1080)
```
so I added "virtual 2048 2048" to my xorg.conf under SubSection "Display" and now when i boot up the resoulution is 1920x1080 without creating a new mode and i can move the mouse over the whole screen. But the desktop is still 1440x1050 that is wierd. But if I change res to 1280x720 and then back to 1920x1080 ```
xrandr -s 1280x720
xrandr -s 1920x1080
``` the desktop will also be 1920x1080. So i added both those lines to my gmd startup script and it works, but the automatic login wont work now and i don't know why. Maybe i should write a script that runs after gdm have logged in and it will work.

Is it ok to do it this way or will cause any problems?

---

### Post by robert35 on 2011-04-06
Thanks a lot for sharing this great information for the force resolution.

---

### Post by Krytarik on 2011-04-06
- "Virtual 2048 2048" seems to be a valid workaround for the mentioned issue.

- Did you add the commands I stated to the GDM startup script?

- Make sure that they are at the right position, like described in the guide I posted.

- Regarding the autologin issue, please post your "/etc/gdm/custom.conf".

---

### Post by ryezs on 2011-04-07
> **Krytarik said:**
> 
- Did you add the commands I stated to the GDM startup script?

- Make sure that they are at the right position, like described in the guide I posted.

Not really when I do this ```

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DFP2 1920x1080_60.00
xrandr --output DFP2 --mode 1920x1080_60.00

```
I get out of bounds on the screen , but i have tested some more and 1920x1080 mode exists when the screen is plugged in so i don't have to add it. I think the problem is when the screen is unplugged. My xrandr looks like this when the screen is unplugged and after the screen is plugged in.
```
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1400x1050      60.0  
   1280x1024      60.0     47.0     43.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       60.0     47.0     43.0  
   1280x768       59.9     56.0  
   1280x720       60.0     50.0  
   1024x768       60.0     43.5  
   800x600        60.3     56.2     47.0  
   720x480        60.0  
   640x480        60.0  
CRT2 disconnected (normal left inverted right x axis y axis)

AFTER:
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 2048 x 2048
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1776x1000      60.0 +
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       75.0     60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x480        60.0  
   640x480        75.0     60.0  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)

``` 
It says that the screen is in 1920x1080 and the screen receives that signal but the desktop is only in 1400x1050. If i try to create and add a new mode at startup it wont work cause DFP2 is disconnected. I have tried to force disconnect CRT1 but it didn't help. It is like gnome desktop don't follow the resolution change. If I change the resolution to something and then back to 1920x1080 the desktop will follow the change but only if i chage to something else first. Is there a way to run a script everytime the DFP2 connects or disconnects?


> **Krytarik said:**
> 
- Regarding the autologin issue, please post your "/etc/gdm/custom.conf".

```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=maskinen
TimedLoginEnable=false
TimedLogin=maskinen
TimedLoginDelay=10
DefaultSession=gnome
```
I'm guessing the auto login issue was caused because i tried to add a mode to DFP2 when it was disconnected and when i tried to change to a resolution that CRT1 didn't support.

---

### Post by Krytarik on 2011-04-07
> **ryezs said:**
> I'm guessing the auto login issue was caused because i tried to add a mode to DFP2 when it was disconnected and when i tried to change to a resolution that CRT1 didn't support.
Yeah, I also guess so. Just now I noticed that you didn't specify an output with these commands:
> **ryezs said:**
> ```
xrandr -s 1280x720
xrandr -s 1920x1080
```
Thus they are getting applied to the currently first output. And it wouldn't affect your external monitor anyway, because it hasn't been connected at that time.

This is also the reason why the desktop is at a lower resolution when you login.

Why do you need to connect the monitor only *after* startup in the first place?

---

### Post by ryezs on 2011-04-08
Do you have any idea why the screen get a out of bounds when i try to select the mode that i have added? I have tried to disable CRT1 output in a script that runs at start up but i didn't help. I have also tried to add 1920x1080 to CRT1 in that script and thought that if CRT1 had 1920x1080 the desktop would be able to change to it.

Is there a way to listen to the monitor changes. If it is I can solve it that way and run a script when the monitor connects

> **Krytarik said:**
> Why do you need to connect the monitor only *after* startup in the first place?
It is a computer that is running a program that i made. And when people are borrowing it they start it without the screen and then calls me and ask what is the problem so if I solve this problem they won't call me about that : )

---

### Post by Krytarik on 2011-04-08
> **ryezs said:**
> Do you have any idea why the screen get a out of bounds when i try to select the mode that i have added?On which monitor, the CRT1 that doesn't support those resolution or the DFP2?

Please connect the DFP2 and run the previously stated commands from within your session. If they change the screen resolution of the desktop as specified, then we know that they work when the monitor is connected.
> **ryezs said:**
> 
Is there a way to listen to the monitor changes. If it is I can solve it that way and run a script when the monitor connects
> **ryezs said:**
> 
It is a computer that is running a program that i made. And when people are borrowing it they start it without the screen and then calls me and ask what is the problem so if I solve this problem they won't call me about that : )
So, basically you are searching for a way to check on boot or on demand if DFP2 is connected, and if so set the desired screen resolution, right? If so, see my earlier post regarding the same matter:
[http://ubuntuforums.org/showthread.php?t=1712863](http://ubuntuforums.org/showthread.php?t=1712863)

---

### Post by ryezs on 2011-04-08
> **Krytarik said:**
> On which monitor, the CRT1 that doesn't support those resolution or the DFP2?
I only have one monitor but the xrander tells me that CRT1 is connected when no monitor is connected that is the weird thing. if you look at my previous post with the xrandr outputs you can see that CRT1 is connected according to xrandr when actually no monitor is connected. 

I get out of bounds when use the mode that i have made with DFP2. I use the modelline from cvt 1920 1080 60 when i crate the new mode.


I'm going to read you other thread se if i will help me, I already have a script that checks what monitor is plugged in at startup so if i'm lucky i just need to rewrite it.

---

### Post by Krytarik on 2011-04-08
> **ryezs said:**
> I only have one monitor but the xrander tells me that CRT1 is connected when no monitor is connected that is the weird thing. if you look at my previous post with the xrandr outputs you can see that CRT1 is connected according to xrandr when actually no monitor is connected.Wow, that's really weird then! Then you did run the first xrandr status blindly?
> **ryezs said:**
> 
I get out of bounds when use the mode that i have made with DFP2. I use the modelline from cvt 1920 1080 60 when i crate the new mode.The cause of both issues may be an incompatibility between the proprietary driver and xrandr.  At my system I'm running the proprietary Nvidia driver, and xrandr  reports a completely different video mode.

---

### Post by ryezs on 2011-04-09
> **Krytarik said:**
> Wow, that's really weird then! Then you did run the first xrandr status blindly? I wrote a script that runs xrandr at startup and saves it to a file.

> **Krytarik said:**
> The cause of both issues may be an incompatibility between the proprietary driver and xrandr.  At my system I'm running the proprietary Nvidia driver, and xrandr  reports a completely different video mode. I will try with another graphics card this weekend, I don't have any nvidia but i have newer amd cards.Maybe it is my card that is the problem.

---

### Post by ryezs on 2011-04-26
It seems that it is a graphics card problem i get diffrent results with different cards so i'm marking this as solved anyway and i will have to fix the problem different for every card

---

### Post by lukax on 2012-04-23
Hey guys,
I'm having the same problem my monitor is full HD but the resolution 1920x1080 doesn't appears..
Xrandr works forcing the resolution to 1920x1080..
But when I install the ati driver xrandr doesn't work anymore, can u guys help me out please???
ps: I looked at the aticonfig documentation and I couldn't find a way to force the 1920x1080 res..
And in Windows I manage to solve this problem in the ATI catalyst control center I did uncheck the use EDID option and did choose the HD resolution..
[IMG]http://i.imgur.com/pNY7p.jpg[/IMG]

I'm still learning english so please don't mind it

---

### Post by ryezs on 2012-06-12
> **lukax said:**
> Hey guys,
I'm having the same problem my monitor is full HD but the resolution 1920x1080 doesn't appears..
Xrandr works forcing the resolution to 1920x1080..
But when I install the ati driver xrandr doesn't work anymore, can u guys help me out please???
ps: I looked at the aticonfig documentation and I couldn't find a way to force the 1920x1080 res..
And in Windows I manage to solve this problem in the ATI catalyst control center I did uncheck the use EDID option and did choose the HD resolution..
[IMG]http://i.imgur.com/pNY7p.jpg[/IMG]

I'm still learning english so please don't mind it

Try adding
```
SubSection "Display"
virtual 2048 2048
EndSubSection
```

under SectionScreen in xorg.conf

---

