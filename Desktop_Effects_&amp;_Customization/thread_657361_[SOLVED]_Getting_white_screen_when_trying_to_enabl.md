---
title: "[SOLVED] Getting white screen when trying to enable visual effects with NVIDIA 169.07"
date: 2008-01-03
forum: Desktop Effects &amp; Customization
---

### Post by ikgo on 2008-01-03
Greetings people!

I just got the NVIDIA 169.07 drivers to work on my 8800 GTS 512, and wanted to turn on the visual effects. All I got was my screen going white and then after ~30 secs. it went back choosing "None".

This is the first time I've tried this distro and Linux, and I've been having quite a lot of fun already installing it on this system.
Well, it's not exactly my first time using Linux, but it's been a few year so I'm basically starting from scratch. I just got the 32-bit version working my laptop with wireless and graphics and all, so everything is possible! ;)
Now I just finished installing the 64-bit version on my main desktop which is running an Intel Q6600 processor. I'm also running:

1) SATA RAID 0 dual-booting with M$ Windows XP.
2) 2x GeForce 8800 GTS 512 configured in SLI.
3) When I get the graphics to work properly I'll be trying to install my X-Fi Elite Pro using the (apparently) crappy drivers Creative released for the 64-bit platform.

I've been having some issues installing the graphics and my guess is that the G92 may not be fully supported yet. But I'm getting there... :)
When I booted up for the first time my system was hanging at "running local boot scripts" so I read [_here_]("http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation") somewhere that I had to
```
sudo apt-get install nvidia-glx-new
startx
```
this one time before I would be asked to enable the restricted drivers. (However, I had to "startx" every time to get up the graphical interface.) Then when I booted up I wasn't asked to install or enable any restricted drivers - nor could I when trying to from System->Preferences->Appearance. I also couldn't choose to shutdown - the buttons for shutdown and restart were gone, so I had to logout and stop GDM and reboot.

But first trying to solve the graphics-related problems, I searched the net and tried a few different approaches, installing the compiz manager, some different libraries, some build-essentials, and finally I tried installing the latest NVIDIA graphics driver. It installed and the hanging at the "running local boot scripts" disappeared.

So saying to myself I was invincible, i tried enabling visual effects again. Then nemesis hit me and I'm now stuck with this white, blanc screen appearing and no error messages...

Any hint you guys might have will be greatly appreciated. :)


- Jon

---

### Post by gurth4ng on 2008-01-04
if u cant login now cuz of the white screen, u can do the folowing to disable visual effects:

at the login screen, click Options
click "select season"
click "failsafe GNOME"

now i'm guessing you wont get the white screen, and u can go in your Appearance options and disable visual effects.

However, i cant tell u how to fix the problem.. i was stuck with a white screen to, and after doing what i just told u and loging back in with a normal Gnome season and trying to re-enable visual effects, i'm getting an error saying "Failed to excecute child proccess "Compiz": Permition Denied".

i've got a topic asking for help on that here [http://ubuntuforums.org/showthread.php?t=631210](http://ubuntuforums.org/showthread.php?t=631210)

---

### Post by ikgo on 2008-01-04
Okay. Thanks for the reply!

However, I got Compiz to work by reinstalling Ubuntu and taking a different approach than last time.

Here's what I did:

[LIST=1]
[*]I followed this [_guide_]("http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation#Booting_to_the_live_CD_with_Radeon_X1800") to install Ubuntu onto my raid 0 array. But at the "Booting to the live CD with Radeon X1800" section I only did ```
startx
``` and didn't try to install any graphics driver at that point. Then rebooted after successfully installing Ubuntu and configuring GRUB.


[*]When my newly installed Ubuntu had loaded, my system hanged again at ```
running local boot scripts (/etc/rc.local)
``` so I pressed ENTER, logged in and did ```
startx
``` again.


[*]Then I found this [_guide_]("http://compiz.org/NVidia") on compiz.org and followed it, including uninstalling "linux-restricted-modules-2.6.22-14-generic" via Synapsis. Restarted the X-server and guess what? Now it works!
[/LIST]

Now I'll just need to fool around a bit with SLI and my sound card... :popcorn:


- Jon

---

