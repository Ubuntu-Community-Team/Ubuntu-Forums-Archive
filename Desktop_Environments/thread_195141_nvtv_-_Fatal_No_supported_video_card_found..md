---
title: "nvtv - Fatal: No supported video card found."
date: 2006-06-12
forum: Desktop Environments
---

### Post by domstyledesign on 2006-06-12
I have an Nvidia GeForce 5500 w/ tv-out.  I installed nvtv from the repos.  When I run it, I get "Fatal: No supported video card found."

I have the nvidia drivers installed.  I also have GLX and compiz running.  any suggestions?

---

### Post by domstyledesign on 2006-06-12
*bump*

I'd really like to find a solution to this soon.  Any help would be appreciated.

---

### Post by TheSandman on 2006-09-09
I have the exact same problem with the exact same card.

It just ruined a TV evening for me.



Wierd how this seems to work with the exact same card though.

[http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia+tv-out](http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia+tv-out)

---

### Post by marx2k on 2006-11-02
I have a GEForce 6800 and it is also having the SAME EXACT PROBLEM
Anyone have a solution?

---

### Post by CanadianMan on 2006-11-29
I also have a GeForce 6800 and get the same Fatal Error when I try to run nvtv.  Is this a driver issue?  Does anyone have tv-out working on their 6800 and if so can you tell us what driver version your using or a possible fix.

Thanks

---

### Post by k0rv3n on 2006-11-30
I have the same problem but with a 6200.

I think the problem lies in xorg.conf where I find:

Section "Device"
    Identifier     "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Driver         "nvidia"
EndSection

I don't really know if I'm supposed to change it myself to the appropriate card or if the card was supposed to be found when I installed the nvidia drivers

---

### Post by PartisanEntity on 2006-12-05
I have a Gforce Go 6200 and got the same error. It could be that nvtv is only for the open-source nv drivers.

Can anyone confirm? Thanks.

This is also of interest:
[http://www.ubuntuforums.org/showthread.php?t=114425&highlight=nvtv](http://www.ubuntuforums.org/showthread.php?t=114425&highlight=nvtv)

---

### Post by c2483 on 2006-12-08
same
7600gt

---

### Post by Garbaek on 2006-12-11
Listning in
7900GTX

---

### Post by rotten777 on 2006-12-17
Same thing. GeForce 7800GT. nVidia drivers without XGL/Compiz. Very frustrating. 

This TV-output is one of the two final pieces of the move from XP Pro!

This can't possibly be that rare of a setup to be having these kinds of problems.

---

### Post by fincan on 2006-12-18
same here, 7600GT PCI-E

---

### Post by Misuzu on 2007-01-30
bump

same for me, using 7800GT

---

### Post by Rodneyck on 2007-02-01
Same here, 7600gt. I swear nvtv worked on another distro so it must be (k)ubuntu.

---

### Post by mlmurray on 2007-03-06
Same error for me.  nvidia 7100gs.  Anyone?  Anyone?

---

### Post by UberKnight on 2007-03-16
Same error with Nvidia 6600...

Someone please help us so we can have :popcorn: nights again!!

Thanks

---

### Post by themunkee on 2007-03-23
Try this thread:

[http://www.ubuntuforums.org/showthread.php?t=336351](http://www.ubuntuforums.org/showthread.php?t=336351)

I changed the resolution of the TV to 800x600 and changed "ConnectedMonitor" to "UseDisplayDevice"

---

### Post by dboyd13 on 2007-04-30
Nvidia 6600 on Ubuntu 07.04 - NVTV states: "Fatal: No supported video card found. "

Anyone found a fix for this?

---

### Post by ernz on 2007-05-03
Same problem:

GeForce 7600 GT
PCI-E 16x
256 MB
570 MHz

lspci shows:
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

Running nvtv shows:
ernz@ubuntu:~$ nvtv
Fatal: No supported video card found.

Very frustrating, Beryl works great, all my games and the res. is fine. Why doesn't this work?!

---

### Post by hammoudith on 2007-05-05
NVTV shows me the same message too. But i was able to output to tv using nvidia-settings. I have to connect to tv first then restart x server.
Using "sudo nvidia-settings" will run nvidia configuration tool. It will detect the tv then you can then choose your output of choice. You'll have to restart x server if you choose twin view.

Remember to backup xorg.conf because nvidia-settings will overwrite it.

With that said, i dont know whats the use of NVTV.

---

### Post by dboyd13 on 2007-05-06
Initially I tried to get my TV out working without NVTV.... but I ran into issues. I connected my TV then started my machine, opened nvidia-settings and it was able to detect my TV. I saved the settings and restarted X (ctrl-alt-backspace)... and I get no TV output.

Any ideas? Could you pls share your working xorg.conf?

P.S. I did run nvidia-settings via sudo

---

### Post by dboyd13 on 2007-05-13
Any idea's anyone?

---

### Post by puterboy on 2007-06-09
same thing here. 6600gt. i am personally gonna backup my xorg.conf and try to install the official driver from the nvidia site, seeing as the open source drivers i have now do not seem to be working :(

---

### Post by puterboy on 2007-06-09
I seem to have a solution. I'm using a 6600gt on ubuntu 6.06 amd64

First off, i didn't use nvtv. i used envy, which configured all my settings for me. maybe it's cheating, but whatever.....after it installed the packages and stuff i needed, nvtv STILL wouldn't work, despite finally seeing the NVIDIA splash screen. so I went into 

Applications>System Tools>NVIDIA X Server Settings

I went to the X Server Display Configuration, clicked on my TV (which it had never detected before), and configured it (I put my screen to the right of screen 0, my PC monitor. I couldn't apply settings, so I saved it and restarted. It didn't work after restarting my X Server (Ctrl+Alt+Shift+Backspace). I found that the file didn't have the correct permissions, so i used

sudo chmod a+rwx /etc/X11/xorg.conf

to let me write it. I couldn't seem to keep any settings by overwriting the file, so I had to save the xorg.conf from the settings panel on my desktop, open both, and paste over the contents of the old file with the new one. worked like a charm. i'm so newbish, but it works now. any questions, feel free to PM me, i'll try to help as much as I can.

Also, after every reboot of the X server, you need to reconfigure your TV setting in the panel, because if it didn't work, it'll overwrite the settings to where your TV is disabled.

Hope it works!!!

---

### Post by yoshimitsuspeed on 2008-03-22
> **puterboy said:**
> I seem to have a solution. I'm using a 6600gt on ubuntu 6.06 amd64

First off, i didn't use nvtv. i used envy, which configured all my settings for me. maybe it's cheating, but whatever.....after it installed the packages and stuff i needed, nvtv STILL wouldn't work, despite finally seeing the NVIDIA splash screen. so I went into 

Applications>System Tools>NVIDIA X Server Settings

I went to the X Server Display Configuration, clicked on my TV (which it had never detected before), and configured it (I put my screen to the right of screen 0, my PC monitor. I couldn't apply settings, so I saved it and restarted. It didn't work after restarting my X Server (Ctrl+Alt+Shift+Backspace). I found that the file didn't have the correct permissions, so i used

sudo chmod a+rwx /etc/X11/xorg.conf

to let me write it. I couldn't seem to keep any settings by overwriting the file, so I had to save the xorg.conf from the settings panel on my desktop, open both, and paste over the contents of the old file with the new one. worked like a charm. i'm so newbish, but it works now. any questions, feel free to PM me, i'll try to help as much as I can.

Also, after every reboot of the X server, you need to reconfigure your TV setting in the panel, because if it didn't work, it'll overwrite the settings to where your TV is disabled.

Hope it works!!!


Try opening nvidia settings in a terminal
sudo nvidia-settings 
or sudo NVIDIA X Server Settings
This will allow you to save settings
I added nvidia settings to my auto start list. 
IDK if it's the best way but it works. 

I have gotten my tv to work with nvidia-settings but I need overscan mode or something because on my tv the desktop stretches past the edge of the screen. 
Seems like a lot of people are having trouble with this. 

I found this thread but haven't had sucess. 
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)
I think something like this should be plug n play and not such a pain. 
It's just a standard part of the nvidia settings interface in windows.

---

