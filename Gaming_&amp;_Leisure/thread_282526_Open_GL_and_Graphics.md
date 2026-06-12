---
title: "Open GL and Graphics"
date: 2006-10-22
forum: Gaming &amp; Leisure
---

### Post by Zeek00 on 2006-10-22
I downloaded Cedega to run Elder Scrolls Morrowind 3 and Oblivion IV. Upon installing Morrowind I ran it to do a test run. The game was lets just leave it SLOW, to slow to play.

I ran the self test check that comes with Cedega. I failed the OpenGL rendering and 3D Acceleration portions of the tests. I'm running a Nvidia GeForce FX 5200 graphics card. Are there drivers for Ubuntu I need to download and configure to use this graphics card to its fullest extend? How do I solve the OpenGL rendering problem? Is it along the lines of just needing to be updated? If so, how?

Thanks,
Zeek

---

### Post by CatKiller on 2006-10-22
As I understand it, if you type ```
glxinfo | grep render
``` into a terminal and get **direct rendering: Yes** back, then you've got your 3D going on. If you don't, you haven't. Have you installed the proprietary nVidia drivers through Synaptic?

---

### Post by Zeek00 on 2006-10-23
I havn't installed anything from the nVidia website partly becuase i can't figure out which package to download for Ubuntu Linux. If you could go there and give me a link or I can list the option and somone tell me which I need. 

Zeek](*,)

---

### Post by srt4play on 2006-10-23
You don't have to download anything from nvidia's website

Use System --> Administration --> Synaptics Package Manager to install the package nvidia-glx

---

### Post by Zeek00 on 2006-10-23
That should solve my 3D Acceleration problem and get my graphics card fully configured correct? Then How would I burn the bridge of the OpenGL Rendering.

---

### Post by CatKiller on 2006-10-23
> **Zeek00 said:**
> That should solve my 3D Acceleration problem and get my graphics card fully configured correct? Then How would I burn the bridge of the OpenGL Rendering.

They are (effectively) the same thing. Get the hardware 3D on your card working, and you'll have got OpenGL working.

---

### Post by Zeek00 on 2006-10-23
Very cool, I'll try that tonight when I get home and tell you how it goes. Thanks for the help.

---

### Post by Zeek00 on 2006-10-23
How do I change the rendering? I typed:

glxinfo | grep render 

and it told me that the Rendering was set to No, how do I go about changing it to Yes?

---

### Post by CatKiller on 2006-10-23
> **Zeek00 said:**
> How do I change the rendering?

Install the nVidia driver (nvidia-glx) through Synaptic, and then run ```
sudo nvidia-glx-config enable
```

---

### Post by Zeek00 on 2006-10-23
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


Is what I got when i typed :

sudo nvidia-glx-config enable

---

### Post by CatKiller on 2006-10-23
It happens quite a lot. So instead you need to change it manually, as it says. Type the commands ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``` Scroll down until you get to the Device section that defines your graphics card, and change the Driver line to >         Driver          "nvidia"
 Save the file, log out, and press Ctrl-Alt-Backspace to restart X. Hopefully you'll get the nVidia logo splash screen, showing you that it's all working.

---

### Post by Zeek00 on 2006-10-23
lol, nvm got it figured out... pays to actually read it!

---

### Post by Zeek00 on 2006-10-23
So I typed in the command that the error message told me to type in if I though that everything was right and it messed up my X config stuff and now I can't start gnome up and I'm stuck in command line. Any help?

---

### Post by Zeek00 on 2006-10-23
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf

Should I type that command in exactly as you have stated it? Or a specific part? When I try to put in the whole thing it doesn't open up the xorg.conf file so I can change what needs to be changed.

I get an error that directs me to use cp --help to look at the arguments for cp

So a solution that is a little more clear would be sweet... and again thank you very much for you help.

Zeek

---

### Post by CatKiller on 2006-10-23
> **Zeek00 said:**
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf

Should I type that command in exactly as you have stated it? Or a specific part? When I try to put in the whole thing it doesn't open up the xorg.conf file so I can change what needs to be changed.

I get an error that directs me to use cp --help to look at the arguments for cp

It was actually two commands, the first to make a backup copy, and the second to edit it.

> **Zeek00 said:**
> So I typed in the command that the error message told me to type in if I though that everything was right and it messed up my X config stuff and now I can't start gnome up and I'm stuck in command line. Any help?

```
sudo dpkg-reconfigure xserver-xorg
``` will start the X configuration tool. Select the nvidia driver, the resolutions you want, and the refresh rates that your monitor can do when you're asked.

EDIT: If you find yourself at the command line and want to edit a file, you can't use gedit because that's a graphical application. Use ```
sudo nano /etc/X11/xorg.conf
``` instead.

---

### Post by Zeek00 on 2006-10-23
When I originally reconfiged X it made a backup to solve the problem:

sudo cp /var/backups/xorg/xorg.conf /etc/X11/xorg.conf

Now I'm back in X. At stage one.... so what do I need to edit in xorg.conf and where is it. And finally how.

Zeek

---

### Post by shane634 on 2006-10-24
Ok Zeek I have been here many times. First of all get the nvidia drivers from the repos. Then:

  ```
sudo gedit /etc/X11/xorg.conf
```

  Look for this section

  Section "Device"
    Identifier     "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
    Driver         "nvidia"
EndSection

  And make sure your Driver says "nvidia" and not "nv" Your Identifier will of course be your card not mine. Hope this helps.  

 Save your xorg.conf file and restart X with control+alt+backspace or reboot.

---

### Post by shane634 on 2006-10-24
BTW. I have an old TNT2 card and can get ET (enemy territory) running pretty smooth. I only have about 350fps with glxgears -printfps. So your card should handle it no problem. If all this fails get Automatix and let it install the drivers for you. Works a charm.

---

### Post by CatKiller on 2006-10-24
> **Zeek00 said:**
> When I originally reconfiged X it made a backup to solve the problem:

sudo cp /var/backups/xorg/xorg.conf /etc/X11/xorg.conf

Now I'm back in X. At stage one.... so what do I need to edit in xorg.conf and where is it. And finally how.

Zeek

[http://ubuntuforums.org/showpost.php?p=1653987&postcount=11](http://ubuntuforums.org/showpost.php?p=1653987&postcount=11)

---

### Post by Zeek00 on 2006-10-24
solved it on my own, but thank you for the help, that got me started!

---

