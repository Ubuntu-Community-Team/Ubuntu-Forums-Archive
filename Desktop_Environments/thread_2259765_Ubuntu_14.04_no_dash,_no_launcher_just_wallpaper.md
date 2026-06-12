---
title: "Ubuntu 14.04 no dash, no launcher just wallpaper"
date: 2015-01-07
forum: Desktop Environments
---

### Post by TAZ46 on 2015-01-07
Hello everyone, I sure hope someone can help me...I may have broken my 14.04 by removing old kernels when my SSD reported not enough space for a new kernel.

It's been over 3 weeks now and I have yet to find a fix.  My ubuntu 14.04 only boots to my wallpaper, a window opens to report a system problem but I can only go to a "shell" with ctrl+Alt+F1 and cannot get any icons or the top status bar back.  I have tried a unity reset with no luck; made certain the unity plug-in was active in ccsm; and several other potential fixes with no success.  I don't know if the following is of any help but I have seen the error message **opengl is not loaded**. I seem to be going in circles as I have tried the same things expecting different results (sign of insanity?)
I am trying to restore my desktop ubuntu without having to do a reinstallation.  My system is an Intel i7-860 with an AMD graphics card, a Samsumg SSD (O/S) and WD 1 Tb (data) drive.
Any help would be greatly appreciated!

---

### Post by TheFu on 2015-01-07
sudo aptitude install lxde
You might need to install aptitude first. It should recognize any missing dependencies better and doesn't require opengl to work.
At the login screen, there is a gear, click on that and select LXDE.

From there, you can work in a GUI to get Unity back, if you still want it.

---

### Post by grahammechanical on 2015-01-07
Have you tried a different video driver? Does this machine have hybrid graphics by any chance? Did you remove all previous kernels or did you leave 2 kernels? The latest and one earlier kernel? If you have 2 kernels, try loading that slightly older kernel.

To get to system Settings from a desktop with just the wallpaper, right click the wallpaper and select Change Desktop Background.

When the OS reports a system problem it will also offer to provide details of what is causing the problem. 

Regards.

---

### Post by TAZ46 on 2015-01-07
Thank you for the reply and your suggestion.  I am a bit worried about adding another desktop layer as I am not familiar enough with what this could do to the mess I may have created.

I looked at LXDE and it looks like the desktop which may work on my old IBM Thinkpad T42 if it can be installed on a non-PAE cpu.  It also looks like the replacement desktop I should consider for my Intel Core 2 Duo which is starting to show its age...like me.
Thanks TheFu !

---

### Post by TAZ46 on 2015-01-07
Thank you for the reply and suggestions.
I have not tried a different video driver as I am at a loss without without the GUI although I have "played" with the command line I am not very familiar with the cl interface. I have 2 kernels; 3.13.0-40 and 3.13.0-39 and I was able to boot with the 39 kernel but still with no dash or launcher.  What did come back were my desktop folders.  I was also able to right click on my wallpaper and go to "all settings" - something I cannot do with the 40 kernel.  My video card is an AMD/ATI Radeon HD5850 and I am using the proprietary driver.  There are 2 other driver choices : X.OrgXserver or another AMD/ATI fglrx-updates.  Again, I am a bit worried to try them in case I break something else.
I was also able to get details on the system problem - the one that caught my eye is "**Xorg crashed with SIGABRT in amd_xs113_int10_x_inb(**)"  which I will google (your video driver suggestion may be the cure).
Thanks again for the reply grahammechanical!

Looks like I have a long road ahead?!

Another oddity...I can open my desktop folders and files but can only close them by using Alt+F4
There are no window close, minimize, maximize on any of the apps that open to run audio, video, odt files ??

---

### Post by TheFu on 2015-01-07
Those symptoms tell me that X/Windows is running, but the window manager is not.
Probably best to just reinstall it.  Sorry - don't know the package name for Unity-desktop. Haven't used it in years.

You could reinstall the ATI driver too, if you like.
```
sudo apt-get  --reinstall install fglrx 
 export DISPLAY=:0
 fglrxinfo 
```
should do it. Shouldn't do any harm, provided you didn't manually install it like Windows requires. If you used a repository, that will be all that is needed.

---

### Post by TAZ46 on 2015-01-16
Sorry for not getting back sooner...I've been fighting a bad cold.  The video driver I installed was originally done via the GUI.  I did find a suggestion for the "**Xorg crashed with SIGABRT in amd_xs113_int10_x_inb()**" that someone posted and had success with but it did not work for me.  I will try deactivating the proprietary AMD/ATI driver and activating the X.OrgXserver driver to see what happens and report back.
Thank you for the suggestion.

Just tried activating the X.OrgXserver driver with no success - it just reverted back the the AMD/ATI; also tried to install the AMD/ATI update fglrxdriver with the same result.
Running command: **sudo apt-get  --reinstall install fglrx** returned
[B]fglrx: Running module version sanity check - Original module
-No original module exists within this kernel
- Installation
- Installing to /Lib/modules/3.13.0.39-generic/updates/dkms[/B]

My knowledge is very limited so the above is mostly meaningless to me.

I ran your other 2 commands and got the following after the fglrxinfo
[B]display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices. Inc.
OpenGL renderer string: AMD Radeon HD 5800 Series
OpenGL version string: 4.3.12798 Compatibility Profile Context 13.35.1005[/B]

I rebooted but with still no dash or status bar.

One thing I forgot to mention on the onset was that I get the top status bar when I get the login screen. The status bar appears for both kernel 40 and 39 but as soon as I get my desktop wallpaper the top status bar is no longer there.  I never see the left bar with my icons.

---

### Post by TAZ46 on 2015-01-26
I now have some new information which may help someone guide me to a solution for this problem.  I booted into kernel 39 and logged in as a guess & EUREKA I have launchers and a status bar albeit not my personalized ones.  I read somewhere that someone else had tried that and his launchers came back...  Then I logged in as myself just to see what would happen; interestingly the top status bar remained but the launchers were not there although I now had 2 new choices at the top left hand status bar; namely ***Applications*** & ***Places*** and I was able to actually launch apps and go to may data drive.

Is this Unity 2D?

Anyone know how can I get my Unity 3D back??

Thanks for any replies!

---

### Post by TheFu on 2015-01-27
Sounds like your config/settings are screwed. Don't know how this happened, but running different GUIs can do it.  There are many different ways to solve this.  I would create a new account and start copying over settings from ~old-userid/.config/ one at a time to see which break it.

Ok - I really wouldn't do that. I'd just delete ~/.config/ completely and start over clean. I don't care too much about GUI settings.

---

### Post by TAZ46 on 2015-01-27
Things are getting more interesting(?) now; I was able to get my dash and some launcher icons back when I launched ccsm and was able to activate the unity plug-in - something I had done before in a different fashion but it never seemed to work.  I was also able to revive my multiple screens which I really like but now I have a top status bar which is abosolutely blank - no way to even shut down (I do it via the terminal).  I agree with you that my config settings somehow got messed up...are you implying that if I delete my /.config/ Ubuntu will regenerate it?  

I'm at a point where I think my best course is to just back up my data and start from scratch with maybe an O/S which is less prone to this type of mess.  Thanks for your reply!

Last night just before launching a terminal so I could shut down I invoked the "Super Key + S" to see if I had any apps still running...what I noticed gave me a glimmer of hope, with all desktops showing I noticed that the status bar was there with all the information it usually displays (ie. date, time,network connection, ubuntu logo etc) but as soon as I select a desktop I end up with what looks like the status bar but it's totally blank !??  Anyone have an idea how to restore it?
Another oddity...there seems to be a bottom bar which was never there before my problem started; is this possibly another clue to help fix my problem?

---

### Post by TheFu on 2015-01-27
> **TAZ46 said:**
>  I agree with you that my config settings somehow got messed up...are you implying that if I delete my /.config/ Ubuntu will regenerate it?  


Yes, back to the defaults.  And you don't have to delete it if that scares you. Just move it to any different name and logout/login.  You'll see.  Clearly, any personal customizations will be gone.

---

### Post by mc4man on 2015-01-27
You may wish to open ccsm from a terminal & look at the 3rd line about "Profile". It should say "unity", if it says default then that needs to be changed.

---

### Post by TAZ46 on 2015-01-29
Well maybe all is not lost.  I found this link quite useful: [http://askubuntu.com/questions/476930/ubuntu-desktop-does-not-load](http://askubuntu.com/questions/476930/ubuntu-desktop-does-not-load).  It helps to know how to word things properly...which was not my case.
Anyway, what got my desktop back to unity were these two commands:  

[B]dconf reset -f /org/compiz/
setsid unity[/B]

I'm not totally in the clear yet and I'll post my efforts in case it helps anyone with a similar problem.  Those two commands got my unity back but only for kernel 3.13.0-39-generic; now to work on the kernel upgrade that started all this.

---

