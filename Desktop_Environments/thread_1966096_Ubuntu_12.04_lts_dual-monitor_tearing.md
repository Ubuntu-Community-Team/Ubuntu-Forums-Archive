---
title: "Ubuntu 12.04 lts dual-monitor tearing"
date: 2012-04-26
forum: Desktop Environments
---

### Post by alexilni76 on 2012-04-26
When I installed ubuntu 12.04 lts release(no beta) with nvidia 295.40 latest drivers on a single monitor everything worked smoothly.  Moving any application around the screen showed no tearing.  Playing videos in flash, html5, even vlc watching dvd's showed no signs of tearing it just ran smooth like windows 7.  But when i enabled my second monitor by seperate x screens with each monitor 1024x728@60hz with xinerama everything that moved started to show video tearing, from moving applications windows from screen to screen to watching videos.  I also switched to twinview and the same issue.  Sync to VBlank in OpenGL Settings in the Nvidia Driver settings did not help even setting it in compiz did not help.  Removing compiz did nothing.

Afterwards I installed MyUnity to customize unity and when I started the program it says that unity is running in 2d mode not 3d.  Is this some kind of a bug with unity or with xserver not able to use opengl drivers(3d portion) when running dual-monitors?

With fedora 16 kde, the flash, html5, and vlc dvd movies had no video tears but when moving applications like the terminal, calculator, firefox or anything around or from screen to screen it had terrible tears and flickering.

My questions are, is there a fix for to these tears when using dual-monitors in Ubuntu? or is this non-fixable and the way all distro's run?

---

### Post by papibe on 2012-04-26
Hi alexilni76.

I've accomplished no tearing with a couple of computers with Nvidia cards. First of all, AFAIK the Nvidia accelartion framework (VDPAU) it's not supported on Xinerama mode.

I would start by disabling it.

Then take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1390284&highlight=tearing"). Take a look at my post regarding dual monitors ([post #14]("http://ubuntuforums.org/showpost.php?p=9494377&postcount=14")). For extra options check post#4 of this [other]("http://ubuntuforums.org/showthread.php?t=1683875&highlight=nvidia+tearing") thread.

When you have got rid of all tearing, try enabling Xinerama, to see if it works (though I haven't read anything new about it).

I hope that helps, and tell us how it goes.
Regards.

---

### Post by alexilni76 on 2012-04-26
I was trying to delete this thread and but I couldn't, anyway better to save this here for others to see.  

Found the solution.
sudo nano /etc/X11/xorg.conf -> enable composite. 
start compiz-settings and enable Ubuntu Unity Plugin. 
Log Out and Log into "Ubuntu" not "Ubuntu 2d".
Now no more flickering or tearing like before but draws windows slow so lets fix this.
Open nvidia-settings,  in "DFP-O-(Samsung SyncMaster)" disable by unchecking "Force Full GPU Scaling" and change also "GPU Scaling Method" from "Stretched" to "Aspect Ratio Scaled"
Finally, in X Server Display Configuration click "save to x configuration file" which is the /etc/X11/xorg.conf

I hope i did not miss anything.

---

### Post by alexilni76 on 2012-04-26
RE:PAPIBE

Thanks for the reply I appreciate it very much. 
Setting "Sync to Vblank" in OpenGL settings in Nvidia driver makes no difference in Ubuntu 12.04.  I actually unchecked it and it still runs smooth even with the compiz composite refresh rate at the default 50 there is no tearing but I set it to 60 anyway.

Enabling the composite in xorg.conf fixed pretty much the whole issue with some tweaks afterwards made it absolutely 100% smooth.  When I was using fedora 16 kde the composite was enabled in xorg.conf by default and still windows tearing even with all the "sync to vblank" enabled in nvidia and compiz, oh well I'm using ubuntu now and fixed it for this distro.

---

### Post by ScottDeagan on 2012-05-31
For the benefit of those of us who don't know how to set "composite" in xorg.conf, could you please provide step-by-step instructions?

---

### Post by alexilni76 on 2012-06-03
[COLOR=Red]I don't quite remember, don't have ubuntu installed anymore.[/COLOR]  [COLOR=Red]My brain does not function very well in my 30's.[/COLOR]

1. Open Terminal program and type: sudo nano /etc/X11/xorg.conf 
2. Scroll down and find the word "composite" and type either "enable" or "1"[COLOR=Red](if it says "Disabled" than type "Enable" or it says "0" type "1")[/COLOR] and save the changes, instructions how to save and exit shown bottom of terminal. 
3. start compiz-settings and enable Ubuntu Unity Plugin. 
4. Log Out and Log into "Ubuntu" not "Ubuntu 2d".

//Now no more flickering or tearing like before but draws windows slow so lets fix this.//<-this is a comment not instruction.

5.Open nvidia-settings,  in "DFP-O-(Samsung SyncMaster)" disable by  unchecking "Force Full GPU Scaling" and change also "GPU Scaling Method"  from "Stretched" to "Aspect Ratio Scaled"
6.Finally, nvidia settings, in X Server Display Configuration click "save to x configuration file" which is the /etc/X11/xorg.conf

_**Step 5**_ is a big issue, because on the next ubuntu restart those settings are reset autumatically so you have to repeat step 5 again.  I gave up so i never figured out this part i also had to replace my intel motherboard because it fried, bought amd cpu, motherboard, and ram and I just installed windows 7 and left out ubuntu or linux altogether.

---

### Post by ScottDeagan on 2012-06-16
Hey alexilni76 - thanks for the instructions. I didn't have a "composite" entry, so I added an 'extensions' section to the very end of my xorg.conf:

1. Open terminal.
2. sudo vi /etc/X11/xorg.conf
3. Add the following at the very end:

Section "Extensions"
    Option "Composite" "Enable"
EndSection

4. Save file and reboot.

Unfortunately, this hasn't stopped the tearing ;(.

My secondary monitor is a 42-inch Sony TV. If I play a movie on it using Movie Player, there's a very annoying tear about a third of the way down. I really want to try and resolve this issue, even if it means buying a new £400 graphics card (was thinking of trying a Radeon card). Obviously I'd prefer to get my GTX 460 working instead, but if I can't...

---

### Post by alexilni76 on 2012-06-17
This issue is with all nvidia cards.  Get the latest nvidia proprietary drivers.
1. sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
2. sudo apt-get update
3. sudo apt-get install nvidia-current
------------------------------------------------------------------------------
Make sure you have compiz installed and find sync to vblank and enable it.  Find refresh rate in compiz and change it to 60hz, 75hz, or 85hz depending on what your monitor is running.
-------------------------------------------------------------------------------
Follow steps 1 - 6 which pretty much fixes all of it but on restart you have to repeat step 5 because for some reason these setting in step 5 don't get saved on your next restart.  I'm running ati radeon 6570 now and i have a whole bunch of different issues now which i will fix.

I had same issue as you in ubuntu 11.10, 12.04 and fixed it but i would have to repeat step 5.

---

### Post by ScottDeagan on 2012-06-17
[alexilni76]("http://ubuntuforums.org/member.php?u=1567769") - thanks for taking the time to reply. I followed all the steps you mentioned and have the latest drivers (295.59), but I still have "slow tearing". In some circumstances (some videos), I can see the tearing moving very slowly from the top of the screen to the bottom. I really don't understand monitor refresh rates, but if I had to guess, I'd say that my settings are probably slightly out (something like 60.00HZ instead of 59.80HZ).

I went into Windows 7, downloaded "Pheonix", saved a binary copy of the reported EDID from the secondary monitor (a Sony TV), and set that in the "Device" section of my xorg.conf, like so:

Option         "CustomEDID" "DFP-2:/etc/X11/sony.edid"

but this still doesn't get rid of the tearing :(.

I have tried everything to try and get rid of the tearing, but nothing seems to work. I think my TV simply isn't a supported device, which is a shame, as it works perfectly in Windows (so it must be doable somehow - I just don't know how).

---

### Post by alexilni76 on 2012-06-17
I just installed Ubuntu 12.04 on my secondary drive with radeon 6570 and had tearing with this video card as well but it's a lot easier to fix it since it has tear free option on the video drivers.

Did you try to run ubuntu on the primary monitor with the secondary not plugged in? Did you take a look online and find out the sony tv specs and the hz it's supports?  

It's probably best to set up manually in the nvidia driver both monitors to run at 60hz refresh rate.

Than, in **compiz, **under **Composite** option, the **refresh rate** should be set to 60hz.  Than go back into primary compiz menu and select **OpenGL** and make sure you have **Sync to VBlank** checked.  Actually, make sure you have **Sync To VBlank **set in the nvidia driver also it's in there somewhere.

It's best to download and use VLC, atleast with this you can also set the deinterlace options to on which also fixes a lot of video tearing in movies.  Good Luck.

---

