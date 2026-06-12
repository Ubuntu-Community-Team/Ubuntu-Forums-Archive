---
title: "ubuntu 18.04 lightdm xrandr"
date: 2018-11-25
forum: Desktop Environments
---

### Post by sz3bbyla on 2018-11-25
I have ubuntu 18 and lightdm is not starting automatic at boot

my problem look like this:

1.if my monitor is open I can do from another computer with putty

sudo service lightdm start
sudo systemctl start vncserver-x11-serviced.service
 
and I can logon to my ubuntu **in my normal resolution 1900x1080 with vnc**

2.if my monitor is off

I can do the same thing  but when **I open vnc resolution is like 1200x700 and all desktop is very small**

[B]how can i fix this to don't be forced to open that monitor all time when I need vnc?

[/B]
with monitor off
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 0 x 0, current 1920 x 1080, maximum 32768 x 32768
default connected primary 1920x1080+0+0 0mm x 0mm 
1920x1080      0.00*

---

