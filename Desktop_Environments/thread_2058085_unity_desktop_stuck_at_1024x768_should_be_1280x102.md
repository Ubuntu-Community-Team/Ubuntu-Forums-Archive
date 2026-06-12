---
title: "unity desktop stuck at 1024x768 should be 1280x1024"
date: 2012-09-14
forum: Desktop Environments
---

### Post by IlikeMoose on 2012-09-14
hi,

I recently installed 12.04 on a desktop after i got an internal hard drive for it and I'm only getting 1024x768. When i had it previously installed on an external hard drive via a usb docking station i was getting 1280x1024.

I know the monitor does 1280x1024 because i looked it up on the manufacturers website
it's an acer flat panel model # AL1711. I have checked all available settings in nvidia-settings and checked display under system settings which has my monitor incorrectly identified as a laptop screen for some weird reason which on the previous install had it properly listed. I've tried all available drivers, the latest 295.49 being the only driver that lets me have 1024x768 the rest give me 640x480. I have all of the most updated packages including kernels.

nvidia-settings only allows me to select up to 1360x768 and i don't have a widescreen monitor. i have a feeling that my problem may be due to the fact that my display is being identified incorrectly as "laptop" instead of the proper model, but i may be wrong. when i run xrandr it doesn't display the highest resolution here's the output:

```

mike@jarvis:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  

```

I'm running 12.04 64bit
Nvidia driver version 295.49
Nvidia chipset 6150SE nForce 430

i know this monitor for a fact does what i'm trying to get it to do, any help would be most greatly appreciated.

thanks :)

---

### Post by silbar on 2012-09-14
I've got the same problem.  From the System Settings > Display panel, it insists that this machine is a laptop, which it isn't, and 1028x768 is the finest it can be.  However, I know that, at the Lab, our systems guy was able to reset my widescreen monitor (there) to something like 1928x1200.  I just don't know how he did it.

Rico Silbar

Note added, one (or two?) days later: for some reason, as I posted elsewhere, on a restart Saturday morning, 12.04 recognized my Hannspree monitor and set the resolution to 1600x900, as high as it can go.  So, for me at least (but not knowing how) my screen resolution problem is solved.

---

### Post by Epodx64 on 2012-09-15
In the nvidia-settings go to where the resolution is and see if you can manually set your resolution click advanced settings. I haven't used a nvidia card for awhile but that's how I had to do it.

---

### Post by IlikeMoose on 2012-09-15
i've tried that already, it only lets me pick 1360x768 max

---

### Post by zombifier25 on 2012-09-15
You can try running this command:
```
xrandr -s 1280x1024
```

---

### Post by IlikeMoose on 2012-09-15
this is what i get

```

mike@jarvis:~$ xrandr -s 1280x1024
Size 1280x1024 not found in available modes
mike@jarvis:~$ 


```

---

### Post by IlikeMoose on 2012-09-20
my issue is still not fixed, does anyone have any ideas?

---

### Post by houseworkshy on 2012-09-20
Only diagnostic ideas and bump.  See what screen resolution choices you  get running a live session from the cd, that uses the open source  drivers rather than nvidia.  If that gives you the correct resolution  then it would give clues to what is wrong, and suggest a fallback  tempory fix if it's another nvidia/ubuntu problem.  'Another' because on  a fresh release it is almost standard for nvidia not to have caught up  yet, bit odd to have it at the  .1 release stage though.
You could  also try running a live session with a Knoppix dvd/cd, Knoppix is one of  the few distributions which ships with many of the popular drivers on  the disk because it is primarally designed to be run live  [http://www.knoppix.org](http://www.knoppix.org)  It's one of those distributions which is worth  having on the rack anyway, having noticed that the 7.04 came out in  August I'm going to get a recent iso for myself.  A very useful disk which has saved my work several times,  the other end of the 'designed for live use' spectrum to puppy, packed  full of things.  
That rave aside the reason I suggest Knoppix is to check on nvidia drivers on your system without Ubuntu in the picture.  That it would  narrow down the problem further.  If it does work then it's an ubuntu/nvidia problem, if you're lucky something like settings, if not compatability.    If none of them work then it may be some hardware or bios problem.
Sorry  I can't offer a fix but if you try the above you'll have some idea of  which brick in the wall to bang your head against.  Might save a bit of  futile hassle. 
And bump.

---

### Post by jrog on 2012-09-20
A bit of a shot in the dark here, but maybe something like this will work (I've used it to successfully add available resolutions before).

Get the proper ModeLine for the resolution you wish to work with, e.g.:

```
cvt 1280 1024
```

That'll output something like this: 'Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync'. 

Now, copy everything after "Modeline" in the output, and make it into a new mode for xrandr, like so:

```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

Now type just "xrandr" (without the quotes) at the command line and use the output to get the identifier for the connected monitor. The output will look something like this (connected monitor identifier bolded):

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
**LVDS1** connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```

So, the identifier in my case is LVDS1. Now that we have that information, try to use it together with xrandr to add the newly-created mode (that you just made above) for the monitor. Remember to use the correct identifier for your monitor:

```
xrandr --addmode LVDS1 1280x1024_60.00
```

If that all seems to have been okay, try to change to the new mode:

```
xrandr --output LVDS1 --mode 1280x1024_60.00
```

If that works, let us know! It'll only be temporary, but we can make it permanent.

---

### Post by IlikeMoose on 2012-09-21
i didn't get an identifier after i used the --addmode command this is the output i got

mike@jarvis:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  
  1280x1024_60.00 (0x1dd)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
mike@jarvis:~$

---

### Post by jrog on 2012-09-21
> **IlikeMoose said:**
> i didn't get an identifier after i used the --addmode command this is the output i got

mike@jarvis:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  
  1280x1024_60.00 (0x1dd)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
mike@jarvis:~$
Judging from that output, the identifier is "default" (without quotes).

---

### Post by IlikeMoose on 2012-09-21
it didn't work :(
the screen flickered for a second then went back to normal 
here's the output i got from the last command

mike@jarvis:~$ sudo xrandr --output default --mode 1280x1024_60.00
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
mike@jarvis:~$

i just tried it a second time after the current update and this is what i got:

mike@jarvis:~$ xrandr --output default --mode 1280x1024_60.00
xrandr: Failed to get size of gamma for output default
xrandr: screen cannot be larger than 1024x768 (desired size 1280x1024)
mike@jarvis:~$

---

### Post by IlikeMoose on 2012-09-23
i also tried editing xorg.conf with the following:

```
Section "Screen"
     Identifier "Default Screen"
     Monitor    "Configured Monitor"
     Device     "Configured Video Device"
     Subsection "Display"
         Modes      "1280x1024"
     EndSubSection
EndSection

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```

When i rebooted I had the same resolution 1024x768 at the login screen but when I got to the desktop it actually was at the correct resolution for about 2 seconds then it reverted back to 1024x768.

---

### Post by TREESofRIGHTEOUSNESS on 2012-09-23
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

have you tried downloading the latest driver???  that could help.

---

### Post by IlikeMoose on 2012-09-23
I have the newest ubuntu supported driver on my system, I'm afraid I'll break something if I try an unsupported driver, i don't want to go through the hassle of breaking something and reinstalling if it doesn't work.

---

### Post by jrog on 2012-09-23
> **IlikeMoose said:**
> it didn't work :(
the screen flickered for a second then went back to normal 
here's the output i got from the last command

mike@jarvis:~$ sudo xrandr --output default --mode 1280x1024_60.00
xrandr: Failed to get size of gamma for output default
**xrandr: Configure crtc 0 failed**
mike@jarvis:~$

i just tried it a second time after the current update and this is what i got:

mike@jarvis:~$ xrandr --output default --mode 1280x1024_60.00
xrandr: Failed to get size of gamma for output default
xrandr: screen cannot be larger than 1024x768 (desired size 1280x1024)
mike@jarvis:~$
I bolded part of the output above, because I'm thinking that it may have something to do with the issue (although it's odd that you got different output after the update... not sure what to think about that). In any case, can you try my steps again, but do the following two things instead of the last step? (So, this would be after the --addmode step, and replacing the last --output step.)

1. ```
xrandr --verbose
```Under the section of the output that begins with "default connected", look for a line that begins with "CRT:" and remember that number. Use it in the next command.

2. Enter the following command, substituting the number that you got in Step 1 for the '#'.

```
xrandr --crtc CRT# --output default --mode 1280x1024_60.00
```If that doesn't work, you might try substituting CRT# after --output, too (instead of "default"). Finally, it might be that the "xrandr --verbose" command lists multiple CRTS; you might also try the final command with the different CRT #'s. 

I hope that gets you somewhere. If not, I'm suspecting that this is something more nVidia-specific, in which case I won't have much to offer (I have literally never used an nVidia graphics card on my machines). Hopefully others will be able to help you, in that case.

---

### Post by IlikeMoose on 2012-10-18
well i got sick of the problem and installed windows 7 so i could play star wars:the old republic and them i got some malware on my pc which made me come back to linux.

in the meantime i upgraded my video card from a geforce 6150 SE onboard video to a dedicated 1 gig geforce 8400. my monitor is now known as unknown instead of laptop with the latest non-beta drivers and i can get a resolution of 1152x864 which is a little bit closer so i'm going to try all this stuff now with my new video card and see if anything helps :) wish me luck.

---

### Post by IlikeMoose on 2012-10-18
i got to here 

```
mike@Jarvis:~$ xrandr --addmode VGA-0 1280x1024_60.00 
```

and got this output:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30

if anyone has any suggestions, I'm game for trying them.  :guitar:

---

### Post by jrog on 2012-10-18
> **IlikeMoose said:**
> i got to here 

```
mike@Jarvis:~$ xrandr --addmode VGA**-**0 1280x1024_60.00 
```and got this output:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30

if anyone has any suggestions, I'm game for trying them.  :guitar:
See the dash ('-') that I bolded in the command you typed above? Is that supposed to be there? You have 'VGA-0' instead of 'VGA0'. Typically, the identifiers don't have dashes in them. You can check the identifier again by typing just "xrandr" (without the quotes) at the command line and looking for "VGA0" or "VGA-0" -- I'm guessing it's "VGA0", which would mean you have a typo in the command you typed.

---

### Post by IlikeMoose on 2012-10-18
nope the identifier is correct it's VGA-0

---

### Post by IlikeMoose on 2012-10-18
direct from guake:

mike@Jarvis:~$ xrandr
Screen 0: minimum 8 x 8, current 1152 x 864, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0     59.8  
   1152x864       60.0* 
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   512x384       120.0  
   400x300       144.4  
   320x240       120.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
mike@Jarvis:~$

---

### Post by jrog on 2012-10-18
This thread may be of some help to you, I hope: [https://bbs.archlinux.org/viewtopic.php?pid=1118930](https://bbs.archlinux.org/viewtopic.php?pid=1118930)

It appears that there have been changes in the recent nvidia drivers that are creating the problem you are experiencing. The thread above includes some explanations, suggestions, and possible workarounds.

Unfortunately, I have never used an nvidia graphics card, so my limited experience is unlikely to be able to help you much at this point. Hopefully someone else can chime in.

**EDIT:** Also check out this thread; post #2 seems to offer a possible fix: [http://www.nvnews.net/vbulletin/showthread.php?t=187657](http://www.nvnews.net/vbulletin/showthread.php?t=187657). Unfortunately, the fixes require getting down and dirty with /etc/X11/xorg.conf.

---

### Post by nerd65536 on 2012-10-19
The newest Nvidia drivers will reject any resolution that isn't in the monitor's EDID. This means that many standard resolutions won't be available. To fix this behavior, see the thread here:
[http://ubuntuforums.org/showthread.php?p=12304338#post12304338](http://ubuntuforums.org/showthread.php?p=12304338#post12304338)

---

