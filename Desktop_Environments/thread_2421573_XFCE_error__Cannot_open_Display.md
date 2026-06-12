---
title: "XFCE error  Cannot open Display"
date: 2019-06-24
forum: Desktop Environments
---

### Post by ndnd on 2019-06-24
I am relatively new with Ubuntu. I had no problems in the past with XFCE4 but now it is creating this error that I am not able to understand. 

I did the installation of xfce4 (I want to run some GUI appications on Ubuntu server remotely) and in the past xfce4 worked great as it has been super light so I do not wish to go with the desktop option. 

To install I did 
> sudo apt-get install xfce4 xfce4-goodies

Now I already had tight vnc installed (It has worked fine so I don't think there is an issue here) 

When I do login with tightvnc I get a blank screen with X. At the console I get the following 
>  
$startxfce4
/usr/bin/startxfce4: X server already running on display localhost:10.0
xrdb: Resource temporarily unavailable
xrdb: Can't open display 'localhost:10.0'
xfce4-session: Cannot open display: .
Type 'xfce4-session --help' for usage.


I have tried reseting VNC, (I do have X11 forwarding on with Putty) and I also did a reboot of the server. 

Any idea ? This is really frustrating. In case you need more info can you please let me know the exact command for getting that or if there is a command I need to execute please let me know the right syntax. 

I have used and installed xfce4 in the past and never had any problems I just installed and then was able to login with VNC to the GUI session. 

Any help would be greatly appreciated

---

