---
title: "video driver/monitor resolution issue"
date: 2006-04-27
forum: Desktop Environments
---

### Post by Odyssey1942 on 2006-04-27
Greetings, I am a brand new-bie to linux and hopefully soon to be an ex-windows user, so any assistance (and patience) greatly appreciated.

I have successfully installed Ubuntu (don't have CD here and unsure of version, but not more than 6-12 mos old. (If version is important, please guide me on how to find the version number from within Ubuntu)

I have used this new computer at home with a 19" Sceptre lcd monitor and the display worked fine. I brought the computer to the office and first tried on a 17" CRT mon and now a 17" Princeton lcd monitor. Both of these come up in  640 X 480 resolution resulting in a lot of scrolling to see the entire screen.

When I bring up the "System/Preferences/Screen Resolution", the only resolution choice there is 640 X 480, so I am assuming that a video driver for either the monitors or my Chaintech G-Force MX4000 Video card might be needed. Not sure which because the Sceptre 19" lcd monitor worked well at home. This is a tad over my head so if anyone can explain why I am having this problem and guide me to a  solution, I would be most grateful. TIA.

---

### Post by superjet on 2006-04-27
Hi TIA,
 I have been using Linux for about 2 years on and off, and now I am on for good. It is a bit of a challenge, but the Ubuntu forums are great for answers.
  
 Anyhow, to your question. 
If you haven't already, set yourself a root password by typing "sudo passwd" This will allow you to work as a normal user, but when you want you type sudo (Super User Do) at the beginning of a command to execute it as root.

Then you can reconfigure your X-server with this command. "sudo dpkg-reconfigure xserver-xorg"
 You can expermient with settings. I am not a graphic intensive user, so I set mine to "vesa" and it has worked so far.
 Good luck!
 Jamie

---

### Post by Sutekh on 2006-04-27
You should be able to change the available screen resolutions by reconfiguring the X windows server package.

 - First you should change to a virtual terminal, by pressing Alt + F1.  Login with your username/password and enter this command to stop the GUI.
```
sudo /etc/init.d/gdm stop
```
 - enter your user password, when prompted

 - Then use this command to reconfigure the X server, and allow you to choose some more resolutions
```
sudo dpkg-reconfigure xserver-xorg
```
 - you will be asked a long string of questions, pertaining to the input devices, the keyboard/mouse and monitor

 - if unsure about how to answer, just accept the default or suggested value

 - eventually you will come to a screen that allows you to set the sable resolutions, use the arrow keys to select the ones you want, and the space bar to activate the option.

 - Finally, when it's all finished, use this command to start the GUI again
```
sudo /etc/init.d/gdm restart
```


 - As for your video card, you might want to start here for NVIDIA drivers.

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers](http://ubuntuforums.org/showthread.php?t=75074)

 - Method 1 is dead easy to setup, and will get you the v7667 drivers from the Ubuntu repository

 - Method 2 is slightly harder, and will get you the latest (or any) Official NVIDIA driver.

---

### Post by Odyssey1942 on 2006-04-27
Superjet, thanks for yours, and especially yours, Sutekh as it gives me the additional guidance that I doubtless need. I am not at the office now, but will try to work my way through the reconfig tomorrow when I get back there.

---

### Post by Odyssey1942 on 2006-04-28
Having now read the link 
( Ubuntu Forums - HOWTO Latest NVIDIA Drivers ) above, my knees are shaking.

I was encouraged by your: "Method 1 is dead easy to setup, and will get you the v7667 drivers from the Ubuntu repository"

However, one of the first things I read was: "Make sure you have both the Universe and Multiverse repositories enabled." Not to be argumentative, but for someone who is 2 days into their first install, this is pretty intimidating. What in the world is this all about?

Is there any chance you could go through the link, putting yourself in my shoes, and giving a brief explanation (or a link to an explanation) of anything (such as the above) that a beginner will not understand?

Many thanks.

P.S. I am not concerned about having a complete library of drivers for the card, or even the latest, I just want to be able to change the resolution of my Princeton monitor. BTW, how is it that it worked on my Sceptre V7, but not the Princeton (both lcd's)?

---

### Post by Sutekh on 2006-04-28
- I'm not really sure why it worked on one monitor and not the other.  If all you are interested in is changing the resolution, you should be able to accomplish that from the command
```
sudo dpkg-reconfigure xserver-xorg
```
 - The NVIDIA drivers are optional.  I assume that currently the X Windows Server (the gui) is using the OpenSource **nv** drivers.  If you go through the reconfiguring process, you may notice what video driver has been selected.  If the OpenSource drivers work for you, then there isn't really a need to get the Official drivers.  Its even commendable, as the NVIDIA drivers are not free in the truest sense of the word.

 - If you do have problems with the 'nv' drivers then you should consider the NVIDIA drivers

___________________________________________________________________________



 - I will walk through Method 1 if you like.  I can still remember what it was like to use Linux for the first time too, so I know how it can feel.

 - After some reading of the link, I realised that you don't need the **universe** repository enabled.  The drivers that you need to install are available in the **restricted** section of the Ubuntu repositories.    

 - Basically the Ubuntu repositories are large online sources of applications.  The software in these repositories can be downloaded and installed by the command **apt-get** or by using the **Synaptic Package Manager** (in the System -> Administration menu).   

 - It's easier for me to show this process using **apt-get** and the command line.  However should you ever want to install software later, I would recommend Synaptic.  It allows you to browse all the software (there is *a lot*), read about what it does, then install it for you, it's really great.

________

 - Okay, so to get these NVIDIA drivers we will install them using the **apt-get** command.  First open a Terminal (Applications -> Accessories menu) and copy and paste this command in, select it with the mouse and right-click in the Terminal to paste. 
```
sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`
```
 - This command tells apt-get that you want to install 3 packages.  **nvidia-glx** - the actual driver, **nvidia-settings** - a utility to manage the NVIDIA settings, and **linux-restricted-modules-`uname -r`** - this package includes modules for certain hardware, such as nvidia cards, because the modules are not 'free' (as in freedom), they are not installed by default.  The `uname -r` part, is a command that apt-get evaluates to determine the correct restricted modules for your kernel.  If you type```
uname -r
``` at the command prompt, you can find out what kernel version you have for yourself.



 - Once you enter that command, apt-get will go off and download all these packages then install and configure them for you.

________

 - When it is finished you need to copy and paste these commands to modify the configuration file for the X server.   It's been ages since I did this on Breezy, so it may not even be neccessary, as the apt-get process may have correctly configured the X server.  If so don't worry about these commands.  

 - In any case the first command copies the original file to a backup one.  (Linux is case-sensitive so its X11 not x11)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
 - This command opens the configuration file in a text editor (**gedit**)
```
sudo gedit /etc/X11/xorg.conf
```


 - First you need to find the section entitled
```
Section "Module"
```
and comment out (add a # sign to) these lines.  These modules we don't want.
```
#Load "dri"
#Load "GLcore"

```
 - Then you need to add this line to the list, this module we do want.
```
Load "glx"
```


 - Next you need to find the section entitled
```
Section "Device"
```
and change the line containing Driver to be "nvidia", as it is probably "nv"```
Driver "nvidia"
```
 - When these edits are complete, save and exit the file.

________

 - The next step is to create a menu entry for the NVIDIA setting utility.   This command opens a new file for the NVIDIA settings```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```
 - When the editor opens, paste this text in
```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;
```
 - You may be able to determine what the text does.  It creates an entry to go in the Applications - > System Tools menu, titled NVIDIA Settings.  If you hover over the entry, the Comment will popup.  The Exec line is the name of the executable file nvidia-settings (which you can use at the terminal if you want).  If you find a nice icon, you can use Icon line to display it, by using the full path to the icon.


 - Finally, make sure all your applications are saved and closed, then you can restart the X server with Alt + Ctrl + Backspace (this is not a PC restart - Alt+Ctrl+Delete)

 - When X server restarts you should login again, and if everything worked then the NVIDIA splash screen should show up before the desktop.



 - Hope this helps you get it working!

---

### Post by Odyssey1942 on 2006-04-29
Sutekh,

I wish you could have seen my face when I restarted Ubuntu and, lo and behold, upcame the nvidia splash screen and the screen in the desired resolution.

First I tried to do an auto configure, but this had no visible result (although in retrospect, I probably should have restarted after the auto-config, but didn't). So next was to try to work through your guidance on step 1.

I had every confidence that you knew what you were doing, but the reverse is true for myself, so I carefully pasted and copied, double-checked everything, all while holding my breath. That it worked is a real testament to both your knowledge and ability to explain it. I note that, even in the beginner forums, answers to pleas for help often come with the most cryptic of guidance from those offering answers.

So most sincere thanks and gratitude. I hope you will be able to help others as effectively as you have helped me, and that some day (way in the future) that I will be able to do likewise.

Kind regards.

---

### Post by IainWood on 2006-04-29
This looks very like the problems I had look for the 'follow the newbie' post, i tried to write up exactly what i had to do to fix the Nvidia drivers problem from a Noob perspective (i.e. very little terminal stuff)

I think it might be helpful to someone!

---

### Post by Sutekh on 2006-04-29
Hi Odyssey, you are most welcome.  

I'm glad to hear that you were able to get it working.  I'm also glad I didn't leave any typos to trip you up too!

Good luck and have fun with Ubuntu!

---

### Post by dannzo on 2006-04-30
I followed the instructions in post #6 yesterday and it worked ok. Then I decided Gnome wasn't for me and installed Kubuntu 5.1.
Now when I get to the line 
```
sudo gedit /etc/X11/xorg.conf 
```
and swap 

```
sudo gedit /etc/X11/xorg.conf
```
for 

```
sudo kedit /etc/X11/xorg.conf 
```
I get “sudo: kedit: command not found”. Can't get any further than that. 
Any clues?

I'm trying to get a higher resolution than 1024 x 768. 
Installing the Nvidia driver with Ubuntu didn't give me any higher resolution options than 1024 x 768. Although I'd still be interested in getting the driver installed with Kubuntu. As far as screen resolution, It's not the monitor, which is a Dell 17” CRT which will take much higher than 1024 x 768.

TIA

---

### Post by Sutekh on 2006-04-30
Use
```
sudo kwrite /etc/X11/xorg.conf
```
or my editor of choice for these sorts of things
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by dannzo on 2006-04-30
Didn't understand the output from sudo nano /etc/X11/xorg.conf, but sudo kwrite /etc/X11/xorg.conf worked. Thanks 

Just need to work out how to get 1280 x 1024 screen resolution.

---

### Post by dannzo on 2006-04-30
Managed to get 1280 x 1024 by editing xorg.conf file. :)

---

### Post by Sutekh on 2006-04-30
nano is a very sparse text editor, but it part of the default Ubuntu install, and by Ubuntu I mean GNOME Ubuntu, Kubuntu Ubuntu, whatever, nano is part of the install. 

You use it just like a normal editor, but without the mouse.  To save a file use Ctrl + O, and then to exit use Ctrl + X.

Anyway, glad you got the higher resolution working.

---

### Post by jnew96 on 2006-04-30
** Sutekh**, thank you so much for the walk-through. I'm just installing KUbuntu for the first time, branching out from my first foray into Linux, Gentoo. I encountered the same stuck-at-640x480 problem on my LCD as the topic starter, and bumbling with xorg.conf and the reconfiguration script didn't help. But installing the nvidia drivers, as per your instructions, worked like a charm. Thank you!

---

