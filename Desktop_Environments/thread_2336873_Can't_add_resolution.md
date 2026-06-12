---
title: "Can't add resolution"
date: 2016-09-12
forum: Desktop Environments
---

### Post by reversedskies on 2016-09-12
Hell everyone,

I am new to Ubuntu and found that with the latest (proprietary and tested) NVidia driver that somehow my resolution of 1600x900 is not supported in Ubuntu 16.04.

Before i was using this NVidia driver (NVidia binary driver 361.42 proprietary and tested) i could use the 1600x900 resolution, after installing the NVidia driver i couldn't use this resolution anymore.

MY screen is a full HD 1920x1080 which on Windows supports 1600x900 with and without the NVidia driver so i don't know what the problem is here.

I have already tried to add the resolution using the "cvt 1600 900 60" which gave me the following result:
- Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
After adding everything after modeline to the "sudo xrandr --newmode" command (sudo xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync) i got the following message:

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  29
  Current serial number in output stream:  29

So apparently it can't add the resolution somehow.
I don't know what is going on exactly but i would like to add the 1600x900 resolution if possible.



Just in case, the xrandr command showed the following result:
\Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
LVDS-1 connected primary 1360x768+0+0 344mm x 194mm
   1920x1080     60.00 +  59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80*   59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
VGA-1 disconnected
HDMI-1 disconnected
DP-1 disconnected





If anyone knows how i can add this resolution then i would greatly appreciate that.
I already know that my screen and hardware support it but i have a feeling the driver will never let me.

Thanks in advance for any replies.

Greetings

---

