---
title: "External Monitor issue"
date: 2009-05-18
forum: General Help
---

### Post by paradigm2 on 2009-05-18
Hello.  This issue has been causing several other annoying problems for me on my laptop.  Basically I have a laptop with a broken LCD.  The LCD built in to it does not really work at all (you can see it a little bit only, its severely cracked) so I have to use an external Monitor.

Well The problem is that various applications are having problems with this.  For instance cheese works, but all the video is shown on the internal LCD, not the working external monitor.  Also if I play a game like Lincity or Trackballs, upon exit or if it is interrupted the resolution will be all messed up.  I suspect that it is trying to use the broken LCD resolution, when I want it to use the External Monitor resolution.

I've tried playing with Preferences -> Display.

Here is what I have.

Monitor: EPI 16"

Mirror Screens UNchecked.

Resolution 1280x1024(5:4)

Refresh Rate: 60mhz


-----

I try to check "Mirror Screens" which should in theory resolve this, but upon doing so the highest resolution I can get is 1024x768(4:3) and this also tends to break the configuration.

What can I do to fix this?

Ideally I would just like to disable the internal LCD entirely and use only the external.

Any advice?

I suspect that I could turn off autodetect and try to specify things manually in xorg.conf.  Is this correct, will it work?

Surely there must be a more elegant way?

Thanks in advance!

---

### Post by paradigm2 on 2009-05-18
I'm thinking I will need to use xrandr here.

Any hints at all to save me some time and trouble?  Any little thing might help....

Here is the output of 'xrandr -q'

```

me@ubuntu-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1200
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1024x768       85.0 +   85.0     75.0  
   1280x1024      60.0* 
   800x600        85.1     75.0  
   640x480        85.0     75.0     59.9  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

```

VGA-0 looks to be my external monitor.  I would like to completely disable the LCD and have everything stay only on the external.

Researching now (but please help if you can) :)

---

### Post by paradigm2 on 2009-05-18
For any one else wondering,

```

xrandr --output LVDS --off  --output VGA --auto

```

Seems to have shut off the LCD and left the external as it was.   However I am unsure if this fixes the other issues.  My gut feeling is probably not.

---

### Post by paradigm2 on 2009-05-18
Hmmm.

Well in testing there is some progress (the LCD is now off), but still not perfect.

I had to "kill -9" lincity-ng, upon doing so I lost my original resolution of 1280x1024 and it became the next step down 1024x768.  However I was able to successfully just go to Preferences -> Display and change it right back to 1280x1024.

This isn't optimal and it is annoying to have it change resolutions like this.  it should not happen.  Does anyone have any hints or suggestions?  I feel that there is a way to do this the correct and optimal way, I'm just missing something. :)

---

### Post by dootzky on 2009-08-12
hey man - you helped me a lot today - just wanted to say THANKS! :)

cheers, 
dootzky

---

