---
title: "Wolfenstein: Enemy Territory"
date: 2007-10-17
forum: Gaming &amp; Leisure
---

### Post by Kevin Mckalister on 2007-10-17
Hi, I'm new to Linux and I'm having problems with this game: Wolfenstein: Enemy Territory.

This is the site from which I downloaded the game:  [http://www.ogmaciel.com/?p=276](http://www.ogmaciel.com/?p=276)

I followed the instructions precisely as required and the downloading and installation seemed to go smoothly.  However, when I tried to start the game, by opening the console and typing "et", I got this...

> ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/rande/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


At first I was getting another message - something about not having the proper acceleration - so I went to the Synaptic Package Manager and downloaded "nividia-glx" and that's what I got.

I'm a newbie at this and I would really appreciate any help.

Btw, I have a NIVIDIA GEFORCE 4 MX 440 AGP 8x graphics card (in case it's needed) and I'm using Ubuntu 6.10 (I haven't had a chance to update it yet.).

Thanks for taking the time...

---

### Post by carlinuxlearner on 2007-10-17
Your Nvidia driver is not installed correctly. I would advise using "envy" 
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu4_all.deb)
just download it to your Desktop then run this command "cd Desktop" then "sudo dpkg -i envy_0.9.8-0ubuntu4_all.deb" then run this "sudo apt-get install -f" then run "envy -g" and it will pop up with a window, you should be able to do it for there.
If you have any problems just post them here.

C@RL

---

### Post by Kevin Mckalister on 2007-10-17
On that last command I got this...

> bash: envy: command not found

Thanks for the help.

---

### Post by glotz on 2007-10-17
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by carlinuxlearner on 2007-10-17
Hum.. Run these commands again "cd Desktop" then "sudo dpkg -i envy_0.9.8-0ubuntu4_all.deb". Post any errors here.

C@RL

---

### Post by Kevin Mckalister on 2007-10-17
I got this after I put in the second command...

> tar: ./prerm: time stamp 2007-10-17 11:04:35 is 17915.652825 s in the future
tar: ./control: time stamp 2007-10-17 11:04:43 is 17923.652391 s in the future
tar: ./postinst: time stamp 2007-10-17 11:04:35 is 17915.652243 s in the future
tar: ./md5sums: time stamp 2007-10-17 11:04:43 is 17923.652012 s in the future
tar: .: time stamp 2007-10-17 11:04:43 is 17923.651875 s in the future
Selecting previously deselected package envy.
(Reading database ... 93162 files and directories currently installed.)
Unpacking envy (from envy_0.9.8-0ubuntu4_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on python-central (>= 0.5.8); however:
  Version of python-central on system is 0.5.6ubuntu2.
 envy depends on python (>= 2.5); however:
  Version of python on system is 2.4.3-11ubuntu3.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy

I have no idea what's wrong.

---

### Post by carlinuxlearner on 2007-10-17
Run this "sudo apt-get install -f" please post output here.

C@RL

---

### Post by Kevin Mckalister on 2007-10-17
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  fakeroot debhelper xserver-xorg-dev g++-4.1 g++ libstdc++6-4.1-dev envy
  dpkg-dev html2text dh-make dpatch build-essential
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  envy
0 upgraded, 0 newly installed, 1 to remove and 185 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2609kB disk space will be freed.
Do you want to continue [Y/n]? 

Farther?

---

### Post by Kevin Mckalister on 2007-10-17
> (Reading database ... 93506 files and directories currently installed.)
Removing envy ...

...?

---

### Post by carlinuxlearner on 2007-10-17
If you have High-speed and are willing to wait awhile then you can try  this. "sudo apt-get update" then "sudo apt-get upgrade" and then run those first commands again "cd Desktop" then "sudo dpkg -i envy_0.9.8-0ubuntu4_all.deb" then run this "sudo apt-get install -f" then run "envy -g". If not then you can try installing the driver manualy, but I will probably have to tell you how, and I've got to go, but I'll be back later (8:30-10:00).

C@RL

---

### Post by Kevin Mckalister on 2007-10-17
What does this mean...

> @-desktop:~$ cd 
@-desktop:~$ ./et
bash: ./et: No such file or directory

Why?

---

### Post by Kevin Mckalister on 2007-10-17
OK, thanks for the help Carl.

---

### Post by Kevin Mckalister on 2007-10-17
Nvidia legacy drivers(?).

---

### Post by carlinuxlearner on 2007-10-17
Alright, if you want to just install the driver manualy then here is the driver you need: [http://us.download.nvidia.com/XFree86/Linux-x86/96.43.01/NVIDIA-Linux-x86-96.43.01-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.01/NVIDIA-Linux-x86-96.43.01-pkg1.run)
Download that to your desktop, then restart your computer, and at the GRUB boot screen select the "recovery mode" kernel, onec booted exicute this "cd /home/yourusername/Desktop" (replace "youusername" with your user name, and make SURE you capitalize the "D" in "Desktop") then exicute this "sh NVIDIA-Linux-x86-96.43.01-pkg1.run" and you should be able to handle it from there. Post any question of errors here.

C@RL

---

### Post by Kevin Mckalister on 2007-10-18
There were two varieties of recovery mode, one generic the other non.  I  tried them both and I kept getting this message:

> You appear to be running in runlevel 1: this may cause problems.  For example some distributions that use the devfs do not run the devfs daemon in runlevel 1, making it difficult for nvidia-installer to correctly setup the kernel module configuration files.  It is recommended that you quit installation now and switch to runlevel 3 (`telinits3`) before installing.

Quit installation now?  (select `No` to continue installation)

... I ended up clicking `No` and proceeding with the installation.  I thought everything worked out, until I restarted the computer and got this:

> Failed to start the X server [. . . . .] 

I reinstalled Ubuntu 6.10, upgraded it and here I am.

---

### Post by Kevin Mckalister on 2007-10-18
I'm going to follow these instructions since I have to start from the beginning now anyways...

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

I'll keep you posted to let you know how I made out. 

 Thanks for all your help C@rl.

---

### Post by Kevin Mckalister on 2007-10-18
Tutorial,
>    1.Select the System menu at the top of the screen.
   2.  Select Administration then Synaptic Package Manager. Enter your password when prompted.
   3.  In the package manager, select the Settings menu, then Repositories.
   4.  In the Software Preferences dialog that comes up, click the Add button.
   5.  In the Edit Repository dialog, ensure that the Restricted copyright box is checked, then press OK.
   6.  Press OK to close the Software Preferences dialog, when Synaptic asks you to reload the package database, say yes.


Concerns:  After following #3 I get a Software Sources box and I don't understand what it means by "click the Add button", in #4- there is no Add button.  The rest went through alright, I think.

Another part from a Tutorial (instructions following the above)...

> 2.  Find the appropriate package for your kernel. For example, if you have linux-image-amd64-k8 installed, then you should install linux-restricted-modules-amd64-k8. Selecting one will also install nvidia-kernel-common. (Note: you have to select the restricted modules first because the nvidia-glx package automatically installs the i386 one - and if you have a generic kernel image, the X will not work.)

This was already installed...

> linux-image-2.6.17-generic.  Description:  linux kernel image for version 2.6.17 on x86/x86_64

linux-image-2.6.17-12-generic.  Description: same as above.

linux-image-generic.  Description:  generic linux kernel image.

Now for restricted, this was originally installed...

linux-restricted-modules-2.6.17.7-10.1.  Description:  non-free Linux 2.6.17 modules on x86_64 generic.

linux-restricted-modules-2.6.17.8-12.3.  Description:  Same as previous.

There are 2 others and their descriptions are...
> 
Non-free Linux 2.6.17 modules helper script.

Restricted Linux modules for generic kernels.

Because of this:

> (Note: you have to select the restricted modules first because the nvidia-glx package automatically installs the i386 one - and if you have a generic kernel image, the X will not work.)

For some reason I installed...

> linux-restricted-modules-686.  Description:  Obsoleted by: linux-restricted-modules-generic.

I guess my thinking was that X wouldn't work with the number 386 on a generic kernel image - which is what I have (I guess).

So I installed a useless package.  A few other choices,  though I'm not sure, cause I don't have much clue as to what I'm doing....

> linux-restricted-modules-2.6.17.8-11.2.  Description:  none-free Linux 2.6.17 modules on x86_64 generic.

linux-restricted-modules-386.  Version: 2.6.17.12.1.  Description:  restricted Linux modules on 386.

linux-restricted-modules-2.6.17.7-10.1.  Description:  non-free Linux 2.6.17 modules on 386.
Then there are these...
> Nvidia-kernel-source.  Description:  NVIDIA binary kernel module source.

Nvidia-legacy-kernel-source.  Description:  NVIDIA binary `legacy` kernel module source.

Does anyone know what I'm supposed to do?

---

### Post by Kevin Mckalister on 2007-10-18
OMG!!!

NICE!!!~It works:)  (The resolution is a little glitchy, but I think this maybe because I haven't applied the patch yet.)

Thanks guyz!

Feedback would be nice, I still mot sure if I handled this in the most appropriate way.  I'll let you know if the glitchiness doesn't go away.

:)!!!!

---

### Post by Kevin Mckalister on 2007-10-18
Still glitchy and it gets to the point where it's impossible to play... Help?

Can someone please review my last few posts and tell me what I did wrong?

---

### Post by bsmith1051 on 2007-10-18
You realize your video card is probably minimum spec for ET?  So even under ideal circumstances it might not run very well.  You'll certainly want to limit your game resolution and/or quality settings.  But that's all secondary to getting it working.

Not sure if I understood all your recent posts:
Did you get the Nvidia binary driver installed, or are you using the more-generic Restricted Driver version (the comes with Ubuntu 7.04) ?  Honestly, I would skip the 'official' instructions and just go to the Envy homepage and download the .DEB auto-installer for my version of Ubuntu.  The only negative of this is that you then need to remember to uninstall it (both Envy and the Nvidia driver it installed) before doing an Ubuntu upgrade.

---

### Post by Kevin Mckalister on 2007-10-18
Which ones should I delete and which should I install?

---

### Post by Kevin Mckalister on 2007-10-18
bsmith1051,
> You realize your video card is probably minimum spec for ET?

It was working perfectly on a WinXP.

---

### Post by Kevin Mckalister on 2007-10-18
It was working beautifully for 20mins then if screwed up again.

---

### Post by bsmith1051 on 2007-10-19
1. Did you ever clarify which version of Ubuntu you're running?
2. Go into Synaptic and uninstall the 'nvidia-glx' driver you downloaded.
3. If you're running Ubuntu 7.04. go into System > Restricted Drivers, and uncheck the 'Proprietary' video driver if it's enabled.
4. go to the Envy homepage,
    [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
    and scroll down to where it says "Packages for Ubuntu"
5. download the latest version, e.g. envy_0.9.8-0ubuntu8_all.deb (you may have already done this?)
6. wherever you saved the file, simply double-click on it!  it should automatically open in the Ubuntu Package Installer.  Click the 'Install' button and you'll be prompted for the root password.
7. Assuming it installs correctly, now look for it under Applications > System Tools > Envy.  Click on the option to download/install the appropriate Nvidia binary driver.

Hopefully this will get you the best possible version of the Nvidia video driver.   BUT, you also have to remember to run the Envy utility and _uninstall_ the driver before attempting any major-version Ubuntu upgrades, e.g. v7.04 to 7.10.  You would then re-run it again afterwards.
________________

Then again, the fact that your current setup works perfectly for 20 minutes _then_ blows-up indicates that it might not be a driver issue!  Are you sure the fans are all working?

---

### Post by Kevin Mckalister on 2007-10-20
Thanks for replying bsmith1051,
> 1. Did you ever clarify which version of Ubuntu you're running?

Yes, I'm running an updated 6.10 Ubuntu.

> 2. Go into Synaptic and uninstall the 'nvidia-glx' driver you downloaded.

Nvidia-glx isn't working very well, though if I'm lucky on some servers I'm able to play for a good 1/2hour without problems, after that I have to disconnect and then reconnect and more often then not everything is ok for another interval.
Why does this happen? (I read that I need Nvidia-glx in order to play this game.)

> 5. download the latest version, e.g. envy_0.9.8-0ubuntu8_all.deb (you may have already done this?)

Sorta.  I followed the instructions of  another member and I ended up having to reinstall my OS, because X or whatever wasn't working...

> Are you sure the fans are all working?

I can hear them.

If I had Windows there wouldn't be a problem, so I guess my hardware isn't the problem ...?

---

### Post by Kevin Mckalister on 2007-10-20
Package installer - envy...

I'm getting this:  "Error:  Dependency is not satisfiable: python-central"

---

### Post by Kevin Mckalister on 2007-10-20
Console,

> desktop:~$ cd Desktop
desktop:~/Desktop$ sudo dpkg -i envy_0.9.8-0ubuntu4_all.deb
dpkg: error processing envy_0.9.8-0ubuntu4_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 envy_0.9.8-0ubuntu4_all.deb

> -desktop:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Big surprise on that last part...

---

### Post by Kevin Mckalister on 2007-10-21
There's a small fixed box on the side of my screen during play.  I've noticed problems occur when this box disappears.

---

### Post by Kevin Mckalister on 2007-10-21
Please tell me, what does it all mean?

I'm sure you guys would be able to solve this very quickly, so why don't you give me the exact instructions and problems that may or may not arise and if so instructions of how to get by... Is this too much to ask for? (Has my info been sufficient enough?).  It seems that because these questions may seem so obvious to you, you don't want to help directly, am I right?

My last few posts.  When I tried installing envy, it wasn't working, why?  What should I do to make it work the way I want it to work? (lol, well if I don't have a clue how it works in the first place, then ... :))

I just what the game to work.  (without learning how it works - a quick fix.)

And thanks to those who've responded.

---

### Post by bsmith1051 on 2007-10-21
Maybe Envy doesn't support Ubuntu 6.x anymore?

---

### Post by hotboyphil on 2007-11-06
hi i have this problem with wolf ET like it used to run fine but for sum reason keeps saying i disconnected for no reson, i got 10mbps so its not my connection also how do u install the patches i cant seem to be able to open them

---

