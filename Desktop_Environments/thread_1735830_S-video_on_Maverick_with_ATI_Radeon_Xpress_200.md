---
title: "S-video on Maverick with ATI Radeon Xpress 200"
date: 2011-04-21
forum: Desktop Environments
---

### Post by numb3r5ev3n on 2011-04-21
Hello, 

I am attempting to set up a clone display on my s-video enabled TV from an ATI Radeon Xpress 200. I'm currently running Xubuntu 10.10. I've found some info on the net, but nothing seems to be working. 

Here is the script I am trying:

xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --addmode S-video 1280x1024
xrandr --output S-video --same-as VGA-0
xrandr --output S-video --mode 800x600

The first command gave me a blank display, which persisted until I hit ctrl-alt-F1 and rebooted. Executed the next command all right, but the third string gives me this error:

nighttrain@nighttrain:~$ xrandr --addmode S-video 1280x1024
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28

Here is what happens with the rest of it:

nighttrain@nighttrain:~$ xrandr --output S-video --same-as VGA-0
nighttrain@nighttrain:~$ xrandr --output S-video --mode 1280x1024
xrandr: cannot find mode 1280x1024


All I want to do is use my TV as a clone display. I love Ubuntu, but this and some issues I've been having with the NWN client lately are making me consider a switch back to Windoze. Can anyone tell me what I am doing wrong here? Thanks in advance.

---

### Post by Alvasin on 2011-04-22
I have a s-video port on my computer and tv. I am trying to get the  video to go from the computer to the tv with no luck. I have an ati  radeon xpress 200m series display adapter. Is there anything special  that you have to do.

---

### Post by aromo on 2011-04-22
> **numb3r5ev3n said:**
> Hello, 

I am attempting to set up a clone display on my s-video enabled TV from an ATI Radeon Xpress 200. I'm currently running Xubuntu 10.10. I've found some info on the net, but nothing seems to be working. 

Here is the script I am trying:

xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --addmode S-video 1280x1024
xrandr --output S-video --same-as VGA-0
xrandr --output S-video --mode 800x600

The first command gave me a blank display, which persisted until I hit ctrl-alt-F1 and rebooted. Executed the next command all right, but the third string gives me this error:

nighttrain@nighttrain:~$ xrandr --addmode S-video 1280x1024
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28

Here is what happens with the rest of it:

nighttrain@nighttrain:~$ xrandr --output S-video --same-as VGA-0
nighttrain@nighttrain:~$ xrandr --output S-video --mode 1280x1024
xrandr: cannot find mode 1280x1024


All I want to do is use my TV as a clone display. I love Ubuntu, but this and some issues I've been having with the NWN client lately are making me consider a switch back to Windoze. Can anyone tell me what I am doing wrong here? Thanks in advance.

I got the same message at line 3 but I got the picture cloned on the TV:
```
xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --output S-video --same-as VGA-0
xrandr --output S-video --mode 800x600
```

---

