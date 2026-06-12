---
title: "Bizarre nVidia driver issue"
date: 2007-04-29
forum: Desktop Environments
---

### Post by Dorsai on 2007-04-29
Newb alert.

I have installed Feisty on a dual core Pentium 805D with 512m ram and an nVidia 5900 Ultra. I have previously run the Feisty beta without issue including the Beryl desktop. I installed the release version figuring the final would be more stable. 

I am now unable to install the nVidia restricted drivers without X failing to start. Has anyone else seen this behavior ? I have tried the 9631, 9755 and legacy driver but no good. I have to "sudo apt-get --purge remove" the driver and run "dpkg-reconfigure xserver-xorg" to get X to work again. This driving me crazy. Any suggestions ? I'd really like to get Beryl installed again. Thanks. :confused:

---

### Post by earobinson on 2007-04-29
you should be able to click, system -> admin -> ristricted drivers, and that should install it all for you.

---

### Post by Dorsai on 2007-04-29
That was what I did for the first try at getting the restricted driver installed. After rebooting it failed to start X and dumped me to the terminal interface. The two subsequent attempts at installing the restricted drivers were done through Synaptic but ended the same.

---

### Post by fwojciec on 2007-04-29
At some stage before Feisty was officially released the old nvidia driver was split into three different packages:
1. nvidia-glx-legacy (for the oldest nvidia cards)
2. nvidia-glx (most nvidia cards)
3. nvidia-glx-new (the latest nvidia cards)
What is happening, probably, is that Feisty installs a version of the driver which is incorrect for your card.  Try installing different versions, perhaps one of them will work.

EDIT:

Sorry, I've read your post again - I guess you've tried that already.  Another suggestion.
Try doing "dpkg-reconfigure xorg-xserver" to configure xorg manually.

---

### Post by ZeroWing on 2007-04-29
Hehehe....


 I've had the same problem.

 Install Evy's unstable version, to get Nvidia's dependencies quickly, but **[COLOR=red]DO NOT RUN IT![/color]**

 Grab Nvidia's newest binary driver from Nvidia.com

 Rename the bin file to something catchy (so you don't forget the name of the file.

 Shut down GDM(/etc/init.d/gdm stop) . Got to tty 1 (alt+ctrl+F1)

 Cd to your desktop.

 type in sh Catchyname.bin

 The driver installer will complain about missing a kernel module or something. Just click no on it, and (oddly enough) it will install without any issues.

 Start GDM again(/etc/init.d/gdm start)

 Now, the resolution will be dreadfully small, so reconfigure Xorg.

 sudo dpkg-reconfigure xserver-xorg

 And make sure you select your driver. Check the resolutions you want after it asks you about you mouse and keyboard, and select medium when it asks you how you want to configure your monitor. The rest should be easy.

 Restart X. Ctrl+alt+backspace

 Sorry if my little guide sucks, but such is life.

---

### Post by lancest on 2007-04-30
Can't catch meaning of first sentence. Evy?
Same problem as others can't get proprietary drivers for Geforce 7400 working at all (just nv_. I was very surprised by this because everything worked well in two previous installations. Tried installing 2 different drivers from Nvidia but no success. Should be working like before!!! ha ha

---

### Post by ZeroWing on 2007-04-30
> **lancest said:**
> Can't catch meaning of first sentence. Evy?
Same problem as others can't get proprietary drivers for Geforce 7400 working at all (just nv_. I was very surprised by this because everything worked well in two previous installations. Tried installing 2 different drivers from Nvidia but no success. Should be working like before!!! ha ha

 Sorry. Envy's an Nvidia and Ati driver installer. The current version that supports Feisty doesn't work too well, so you shouldn't run it.


 [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by jimbean on 2007-04-30
have you tried automatix

---

### Post by Dorsai on 2007-04-30
Well if life wasn't bizarre enough with the release version of Feisty.

I deleted all of the nvidia drivers off my machine.

I downloaded the latest Envy package and followed the directions.

It installed a bunch of stuff that I have no idea what it was.

I reboot and it looks like the desktop is fine so naturally I assume Envy worked and I now have a working nVidia driver on my rig. Hooray :) 

So I try to start Desktop Effects and............drum roll sounds...........Error message. You need to have  nVidia driver installed, would you like to proceed?

Sure. So I hit  "Ok" and again downloads start happening. Instead of like last time with Envy this is a bigggg file so I can read the package and its the 386 kernel. Damn I know what that means...no more dual core CPU support.

Anyway I let it do its thing figuring this whole install is Borked anyway.

So I reboot and ......drum roll......Error and right back to the command line boot screen. Damn.

Well now Im irate so I figure what the heck....sudo apt-get nvidia-glx-new it is and off we go with another download. This one finishes and I hit CTRL+ALT+DEL and reboot.

I find myself on the Ubuntu login desktop in total disbelief. I login and make it all the way to the desktop. I decide what the heck why not....Desktop Effects it is. Sure'r than Shi!t it fires right up and works like a champ.

So after all of this what have I learned ?

Nothing really, possibly the issue with the latest release and nvidia drivers is somehow part of the "generic" kernel. 

Now the question is am I brave enough to try changing back to the generic kernel to recover my second CPU core ?

Tune in later at this same Bat Channel  for more exciting adventures in Newb land....

---

### Post by FuturePilot on 2007-04-30
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This will reset xorg back to the default configuration.

Here's the run down on the drivers
The Nvidia-glx-new package is the lates driver. The Nvidia-glx package is the 9631 driver which was the last driver that Nvidia provided before they dumped a bunch of cards onto the legacy driver. The reason it's in the repos is so that people that got their card dumped off to the legacy driver can still use a pretty recent driver and not have to resort to that old legacy driver. And finally that legacy driver is for those really old cards. Thankfully that 9631 driver is in  there or else I would have to use that legacy driver.

---

### Post by lancest on 2007-04-30
After new install tried to change 'nv' driver. Installed several proprietary drivers using synaptic. Failure. Tried 3 times no success. Took to reading my Xorg failure screen. Said: '**API mismatch- has 1.0-9755 Nvidia kernal. This X module has version 1.0-9631. Make sure kernel module and driver components are same version**' So I just matched up 9755 kernel with 9755 X driver. Worked perfectly. Ah Relief!!!  [SIZE="4"][COLOR="Green"]Make sure the driver matches the Nvidia kernel module and you will have no problem.[[/COLOR]/SIZE]

---

### Post by Dorsai on 2007-04-30
> **FuturePilot said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This will reset xorg back to the default configuration.

Here's the run down on the drivers
The Nvidia-glx-new package is the lates driver. The Nvidia-glx package is the 9631 driver which was the last driver that Nvidia provided before they dumped a bunch of cards onto the legacy driver. The reason it's in the repos is so that people that got their card dumped off to the legacy driver can still use a pretty recent driver and not have to resort to that old legacy driver. And finally that legacy driver is for those really old cards. Thankfully that 9631 driver is in  there or else I would have to use that legacy driver.

I knew about the driver issues and the ongoing problems with them in the release version of Ubuntu which is why I deleted all of them and took a shot at the Envy tool. 

With the graphic drivers being a mess for both nVidia and ATi and wireless still being hashed up I feel even Ubuntu is still behind Windows for ease of use "out of the box". The release is a big step beyond Linux just a couple years ago but with technology on the march I wonder if Linux will ever be equal to or better than Windows in its support of hardware. Maybe this is about as good as a free OS will ever be.

---

### Post by lancest on 2007-04-30
There should be a driver alert posted somewhere about this! Yes. 
 Linux is cutting edge and but has some complexity. I am grateful for it because it means freedom once I learn.

---

