---
title: "Booting to Command Line"
date: 2011-01-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jaraldo on 2011-01-13
Hello, 
I'm relatively new to Ubuntu and am having an issue.

I installed Ubuntu 10.10 on my Dell Dimension 9150 desktop machine alongside Windows 7. At first everything seemed to be working fine. Ubuntu then updated itself automatically and I installed the graphics driver that it wanted to install and now it boots to the command line. 

I did some reading about it and I input the command 'startx' and I can get the gui to load that way, but I'd rather not have to go through the whole song and dance whenever I reboot the machine. Is there a way to load the gui without having to input 'startx' every single time?

I installed Ubuntu on my Dell Inspiron 6000 laptop (as the only OS) and it is running perfectly fine. I don't understand why I'm having issues with my desktop machine.

Here are the basic the system specs:

Dell Dimension 9150
Processor: Pentium D Dual Core @ 2.8 Ghz
Ram: 4GB
Video: nvidia GeForce 9800 GTX +

I gave Ubuntu a 100 GB partition running alongside Windows 7.


Any help would be appreciated! Thanks!

---

### Post by sikander3786 on 2011-01-13
Welcome to the forums :-)

From the command line, try reconfiguring your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

Note: When it asks for a password, you might not see any asterisks or characters appearing on the screen when you type it. Just type blindly and hit Enter.

---

### Post by Jaraldo on 2011-01-13
I'm not quite sure what that did. I input those commands into the terminal which restarted the machine and it still booted to the command line. I input the 'startx' command again and the gui loaded, but my screen resolution is now low and the desktop visual effects do not work.

I'm assuming that the graphics driver has been removed now. When I attempted to go into the monitor menu to adjust the screen resolution I get the following message:

"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?"

When I say yes I get this message:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server."

Needless to say, I have no idea what this means...

---

### Post by Jaraldo on 2011-01-13
I did a clean install of Ubuntu 10.10 again, installed the graphics driver, and again it boots to the command line. :( It's still quite frustrating. Any additional help would be appreciated.

---

### Post by cipherboy_loc on 2011-01-13
When you get to the command line type:

```

status gdm

```

If it gives you something other than
> 
gdm start/running, process {some number}


than run: 
```

sudo update-rc.d gdm defaults
service gdm start

```

and that should do it. If not, post back.



Cipherboy

---

### Post by sikander3786 on 2011-01-14
Which version of Nvidia drivers did you install? I hope it is the recommended/current one?

Please post the output of this command.

```
cat /etc/X11/xorg.conf
```

---

### Post by Jaraldo on 2011-01-14
> **cipherboy_loc said:**
> When you get to the command line type:

```

status gdm

```

If it gives you something other than


than run: 
```

sudo update-rc.d gdm defaults
service gdm start

```

and that should do it. If not, post back.



Cipherboy

Yeah I did that, and I got what you said I should:

"gdm start/running, process 1136"

---

### Post by Jaraldo on 2011-01-14
> **sikander3786 said:**
> Which version of Nvidia drivers did you install? I hope it is the recommended/current one?

Please post the output of this command.

```
cat /etc/X11/xorg.conf
```



When I input that command, I get:

Section "Screen"
        Identifier    "Default Screen"
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier    "Default Device"
        Driver "nvidia"
        Option "NoLogo"       "True"
EndSection



As it turns out if I let it sit at the command line for about 5 minutes it will eventually load the gui and take me to the graphic log in. However, a 5 minute boot time is really long.

I'm not sure which drivers I installed, but Ubuntu seemed to recognize that I needed a proprietary driver when I installed the OS and I installed that one. I do remember trying to install the latest Linux nvidia driver yesterday before I did another clean install, but honestly I'm so new to Linux that I'm still trying to figure out how to properly run programs and install drivers when I download them from somewhere other than the Ubuntu Software Center.  

Thanks for your help!

---

