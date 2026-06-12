---
title: "GM965 restricted resolutions"
date: 2009-04-15
forum: General Help
---

### Post by Psychopump on 2009-04-15
Hello all,

I have a laptop with 8.10 Intrepid installed on it. The laptop´s motherboard has an Intel GM965 graphics chip on it.

I have the latest intel driver installed from the repository, but have the following issue:

Under XP I was able to get much higher screen resolutions than I am able to now, up to 1600x900.
Now I am limited to 1280x800.

I have read about 915resolution, but that does not seem to be the solution.

Is there any file I can edit to add resolutions to the list of possibilities?

BTW: my xorg.conf file lists no resolutions at all, just that my devices are configured.

---

### Post by Thelasko on 2009-04-15
915resolution is VERY old and outdated.  Your xorg.conf file should not contain any resolutions.  It should be mostly empty by default.

Please open the terminal and type:
> xrandr -q
Then post the output here.

---

### Post by Psychopump on 2009-04-15
> **Thelasko said:**
> 915resolution is VERY old and outdated.  Your xorg.conf file should not contain any resolutions.  It should be mostly empty by default.

Please open the terminal and type:

Then post the output here.

I am at work at the moment, I will post the results of that query as soon as I get home (20:00 GMT).
Thanks!

---

### Post by Psychopump on 2009-04-15
> **Thelasko said:**
> 

Please open the terminal and type:

Then post the output here.



```
loki@loki-laptop:~$ xrandr -q 
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
```

Which seems odd because my screen is NOT square.....LOL

---

### Post by Psychopump on 2009-04-16
*bump*

...in the hope that Thelasco picks this up again. ;)

---

### Post by Thelasko on 2009-04-16
Sorry, I'm back.  It appears that the Intel drivers aren't detecting you screen resolution properly.  This is a bug.  Please file the bug report against the package "xserver-xorg-video-intel" [using these instructions.]("https://help.ubuntu.com/community/ReportingBugs")  You will need to use the command line, but it's very easy.

To work around this bug, you should be able to enter some lines into xorg.conf to override the resolutions the Intel driver has detected. To do so, add the following lines to the "Screen" section of your xorg.conf file. (change nothing else!)

```
       SubSection "Display"
           Depth		24
           Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
           # ADD A VIRTUAL LINE TO PROVIDE FOR THE LARGEST SCREENS YOU WILL HOTPLUG 
           Virtual              2048 2048 
       EndSubSection

```
Substitute the resolutions on the "Modes" line with those appropriate for your monitor.

---

### Post by Psychopump on 2009-04-16
> **Thelasko said:**
> Sorry, I'm back.  It appears that the Intel drivers aren't detecting you screen resolution properly.  This is a bug.  Please file the bug report against the package "xserver-xorg-video-intel" [using these instructions.]("https://help.ubuntu.com/community/ReportingBugs")  You will need to use the command line, but it's very easy.

To work around this bug, you should be able to enter some lines into xorg.conf to override the resolutions the Intel driver has detected. To do so, add the following lines to the "Screen" section of your xorg.conf file. (change nothing else!)

```
       SubSection "Display"
           Depth		24
           Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
           # ADD A VIRTUAL LINE TO PROVIDE FOR THE LARGEST SCREENS YOU WILL HOTPLUG 
           Virtual              2048 2048 
       EndSubSection

```
Substitute the resolutions on the "Modes" line with those appropriate for your monitor.

Thanks a million! I will try this a soon as I get home from work.
I will let you know how it goes...

---

