---
title: "Changing a screen resolution."
date: 2010-12-16
forum: Desktop Environments
---

### Post by profesior on 2010-12-16
Hey, I have installed Ubuntu yesterday and it's a little problem with Gnome. Perfect resolution for my monitor is 1920x1080, but in monitor preferences i have only 1360x768, 848x480 and two 4:3 resolutions. Is there any way to adjut it? thanks ;)

Matt

---

### Post by ivicks on 2010-12-16
what type of video drivers are you using? priority drivers or non-priority.If your not sure you may want to "enable restricted drivers"

System -> Administration -> Hardware drivers

---

### Post by Krytarik on 2010-12-16
> **ivicks said:**
> what type of video drivers are you using? priority drivers or non-priority.If your not sure you may want to "enable restricted drivers"

System -> Administration -> Hardware drivers
+1 for Hardware Drivers

You mean "proprietary drivers" (closed source)!! :D

---

### Post by SpotHT on 2010-12-16
You can use **xrandr **to add undetected screen resolution. You simply need to issue this command:[INDENT]**```
****xrandr --addmode VGA 1920x1080
```**[/INDENT]For more information, check this [link]("https://wiki.ubuntu.com/X/Config/Resolution").

---

### Post by Krytarik on 2010-12-16
> **SpotHT said:**
> You can use **xrandr **to add undetected screen resolution. You simply need to issue this command:[INDENT]```
**xrandr --addmode VGA 1920x1080**
```[/INDENT]For more information, check this [link]("https://wiki.ubuntu.com/X/Config/Resolution").
That only affects the desktop.;)

EDIT: Oops, confounded this with another thread. I would check "Hardware Drivers" before.

---

### Post by profesior on 2010-12-18
In System>Administration>Drivers I haven't got anything. It works with gigabyte 6-quad s-series GA-G31M-E52C Motherboard as a integrated video card.

---

### Post by Krytarik on 2010-12-18
It's ok then. You may try adding the desired resolution like SpotHT mentioned:
```
xrandr --addmode VGA 1920x1080
```or check beforehand if your chip supports that resolution:
```
sudo apt-get install hwinfo
sudo hwinfo --framebuffer
```EDIT: After you've done that and the resolution works, you have to make the change permanent. I'd recommend to change/add an entry in your /etc/X11/xorg.conf:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")

---

### Post by profesior on 2010-12-18
Look at this:
```
james  @ james-desktop: ~ $  sudo apt-get  install hwinfo v86d
 Reading package lists ...  Done
 Building dependency  tree
 Reading state information ...  Done
 Will be installed  following packages:
   libhd16
 Will be installed following  packages:
   hwinfo libhd16  v86d
 0 upgraded,  3 newly installed, 0  to remove and 348 not  upgraded.
 E: Could  not get lock / var /  cache / apt /  archives / lock -  open (11:  Resource temporarily unavailable)
 E:  Unable to lock the download  directory
 james @ james-desktop: ~  $
```It has translated by Google form Polish language.

Do you know, how can I install hwinfo x86d by other method?

---

### Post by Krytarik on 2010-12-18
Shall I write in german?

As I figured, you don't necessarily have to check your supported video-modes with hwinfo, because it's obviously not reporting all of them. Just go ahead with xrandr.

The error-message suggests that you are running another package-mangager at the same time, e.g. Synaptic.

---

### Post by Krytarik on 2010-12-18
As I followed the guide I figured one thing:

If you are about to create a "Modeline" and you want to specify a refresh rate (Hz) (for my CRT I have to of course, since otherwise it's flickering), the default of the cvt-command is 60 Hz, you have to modify the command like this, e.g. for 85 Hz:
```
cvt 1152 864 85
```

---

### Post by profesior on 2010-12-18
> Shall I write in german?I think that's better for other users to write in English, some users can have similar problems like that. You can help them:) 

I have typed ```
 xrandr --addmode VGA 1920x1080
```and I have ```
 xrandr: cannot find output "VGA" 
```

Ok, ok. In my computer isn't VGA but VGA1 ;)
--addmode doesn't work.
```
xrandr: cannot find mode "1920x1080"
```

---

### Post by Krytarik on 2010-12-18
How is your monitor connected to your machine?

What is the output of
```
xrandr
```

You may also try to skip the xrandr-part and go directly to the configuration of xorg.conf, but that would be risky because you don't know if the video-mode ist supported by your video-chip. Then I would at least check with "hwinfo" before.

---

### Post by Krytarik on 2010-12-18
> **profesior said:**
> I think that's better for other users to write in English, some users can have similar problems like that. You can help them:) 

I have typed ```
 xrandr --addmode VGA 1920x1080
```and I have ```
 xrandr: cannot find output "VGA" 
```Ok, ok. In my computer isn't VGA but VGA1 ;)
--addmode doesn't work.
```
xrandr: cannot find mode "1920x1080"
```
I didn't see that you've edited your post. Then you have to add the "Modeline" like described at the link I posted.

---

### Post by profesior on 2010-12-18
You gave me a link:
[https://wiki.ubuntu.com/X/Config/Res...%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")                                                                 
I've read there how to add undetected resolution.
Modeline "1920x1080_60.00" wasn't  exist, because it hadn't detected. So, I typed:
```
 $ cvt  1920 1080
```There was sth like this
```
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00   2048 2248 2576   1083 1088 1120 -hsync +vsync
```Next, I created new modeline:
```
$ xrandr --newmodeline "1920x1080_60.00"  173.00  2048 2248 2576  1083 1088 1120 
-hsync +vsync
```And , at the end:
```
$ xrandr --addmodeline "1920x1080_60"
```In** System -> Preferences -> Monitors**  showed new screen resolution.I've chosen 1920x1080 and enjoy good resolution :) Thanks for help.
Ein Bier fur Dich ;)

---

### Post by Krytarik on 2010-12-18
Are you using an LCD, since you only have added a video mode with 60 Hz refresh rate, I mentioned it earlier.

And you're not already done, you still have to do the xorg.conf-part. Because when you reboot at this state, the resolution will be reset!

---

### Post by profesior on 2010-12-18
Yes, I know. That's no problem ;)

---

### Post by Krytarik on 2010-12-18
Have a nice (winter)day then, bye!

---

### Post by ciruman on 2010-12-19
Thank's It worked for me too.

Well done!!!!:

```
cvt  1920 1080

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

xrandr --addmode VGA1 "1920x1080_60.00"
```

---

