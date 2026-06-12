---
title: "Automate nvidia-settings for docking/undocking?"
date: 2009-04-11
forum: General Help
---

### Post by psycovic23 on 2009-04-11
Hey,

Every time I dock my laptop, I have to manually go into nvidia-settings and set the resolution and such. Is there any way I can write a script that automatically does the switch when I undock/dock?

---

### Post by quazi on 2009-04-11
> **psycovic23 said:**
> Hey,

Every time I dock my laptop, I have to manually go into nvidia-settings and set the resolution and such. Is there any way I can write a script that automatically does the switch when I undock/dock?

Check out the utility disper, which makes this process really easy.
```
sudo aptitude install disper
```

---

### Post by psycovic23 on 2009-04-11
Is it in the repositories? Aptitude couldn't find it, and the main page for the program is down.

---

### Post by quazi on 2009-04-12
No, I'm sorry, here's the repository:

[https://launchpad.net/~wvengen/+archive/ppa](https://launchpad.net/~wvengen/+archive/ppa)

---

### Post by psycovic23 on 2009-04-12
Alright, problem solved! I ended up writing a bash script that tests to see what my current resolution is and if my Thinkpad T61p is docked. 

```

  1 #!/bin/bash
  2 while true; do
  3 res=`xrandr | grep 'current' | awk '{ print $8}'`
  4 docked=`cat /sys/devices/platform/dock.0/docked`
  5 if [ $res == '1400' ]
  6         then if [ $docked == '1' ]
  7                 then disper -d DFP-1 -r 1280x1024 -s
  8         fi
  9 fi
 10 if [ $res == '1280' ]
 11         then if [ $docked == '0' ]
 12                 then disper -d auto -r 1400x1050 -s
 13         fi
 14 fi
 15 sleep 10
 16 done


```

Thanks!

---

### Post by yuki000 on 2009-05-24
HP Pavilion 6835 with Nvidia driver Ubuntu Jaunty and XBMC (Xbox media center)
with this script I use the laptop has a media center in my tv using the HDMI cable if you startup ubuntu with hdmi cable internal monitor turn off and HDMI out turn on or without HDMI cable internal monitor on hdmi off

hi this is my script, I mixed this and another one from the web to fit in my laptop thanks

[http://onlyubuntu.blogspot.com/2009/04/autodetecting-and-configuring-multiple.html](http://onlyubuntu.blogspot.com/2009/04/autodetecting-and-configuring-multiple.html)

remember to check monitor.sh rights 
chmod 755 monitor.sh

#!/bin/sh
#
# Detect displays and move panels to the primary display
#

# disper command will detect and configure monitors
disper --displays=auto -e

# parse output from disper tool how many displays we have attached
# disper prints 2 lines per displer
lines=`disper -l|wc -l`

display_count=$((lines / 2))

echo $display_count

echo "Detected display count:" $display_count

# Make sure that we move panels to the correct display based
# on the display count
if [ $display_count = 1 ] ; then
echo "Moving panels to the internal LCD display"
disper -d DFP-0 -r 1280x800 -s
else
echo "Moving panels to the external display"
disper -d DFP-1 -r 1280x720 -s
# here is my external HD TV resolution 1280x720 
# for full HD Tv's is 1920x1080
fi

---

### Post by klemi on 2009-07-07
Hallo Youki000,

I have some question to your configuration,

I will do the same as you with my laptop and external monitor.
Do you insert the names of the attached displays in gconf-editor --> panel --> toplevels?

With enter by:

```
klemens@klemens-laptop:~$ disper -l
display DFP-0: LPL
 resolutions: 320x240, 400x300, 512x384, 576x432, 680x384, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 960x600, 1024x768, 1152x864, 1360x768, 1440x900
display DFP-2: HP LP2475w
 resolutions: 320x175, 320x200, 360x200, 320x240, 400x300, 416x312, 512x384, 640x350, 576x432, 640x400, 680x384, 720x400, 640x480, 720x450, 640x512, 720x480, 700x525, 800x512, 720x576, 840x525, 800x600, 960x540, 832x624, 960x600, 896x672, 928x696, 960x720, 1024x768, 1280x720, 1152x864, 1360x768, 1280x960, 1440x900, 1280x1024, 1400x1050, 1600x1000, 1600x1024, 1680x1050, 1600x1200, 1920x1080, 1920x1200
klemens@klemens-laptop:~$
```

Have I insert in Gnome panel the value DFP-0 and DFP-2 in this case?

Have you practice the nvidia-tool nvidia-settings to configure the xorg.conf?
Can you post your xorg.conf, please?

Can I do my autodedecting and configuration multiple monitors with single display configuration with laptop-display?

On which place (Ubuntu) have you insert your script ?

Thanks very much

Klemi

---

### Post by dpb on 2010-12-09
Thanks so much for posting this!  Disper works great. I'm using it on 10.10 with no issues.

---

