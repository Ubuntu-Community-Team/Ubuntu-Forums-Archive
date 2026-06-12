---
title: "Force boot to safe mode?"
date: 2005-03-14
forum: Desktop Environments
---

### Post by marcadams on 2005-03-14
Hi everyone;

I installed the Hoary preview and everything was great..until I installed the NVIDIA driver...now on boot the NVIDIA splash screen starts, but it never goes away - so I cannot do anything !!! It also sometimes causes me to loose Bios settings on my motherboard after I have rebooted...grrrr...

Looking at other threads I see there has been some issues here.

Problem is I have autolog-on enabled, so I cannot turn it off! Hence machine locks everytime...douh!


Could someone please tell me how to force Ubuntu to start in safe terminal mode - so I can uninstall the NVIDIA drivers?? 
Or do I have any other options??


Many thanks
Marc

---

### Post by hashimoto on 2005-03-14
To enter Grub menu you got to push ESC when your PC boots. There you can select the safe mode.

---

### Post by marcadams on 2005-03-14
Wow...thanks for the quick reply....I had only just finished the post! !

Thanks very much
Marc

---

### Post by marcadams on 2005-03-15
Hi;

After hitting ESC, I was eventually taken to the command prompt. 

What I *really* want to do is uninstal the NVIDIA drivers. Please can someone tell me how to do it from this command prompt.

Alternatively, could some please tell me how to boot into a safe GUI mode - I.e. a mode which does not load any of the drivers. 
(REMEMBER I currently have autolog-on enabled !!)


I really don't want to sit and look at nothing but the NVIDIA splash screen for another night  =; 



Thanks very much for anybody's help
Marc

---

### Post by iomicifikko on 2005-03-15
[QUOTE=marcadams]Hi;

After hitting ESC, I was eventually taken to the command prompt. 

What I *really* want to do is uninstal the NVIDIA drivers. Please can someone tell me how to do it from this command prompt.

Alternatively, could some please tell me how to boot into a safe GUI mode - I.e. a mode which does not load any of the drivers. 
(REMEMBER I currently have autolog-on enabled !!)


I really don't want to sit and look at nothing but the NVIDIA splash screen for another night  =; 



Thanks very much for anybody's help
Marc[/QUOTE]
 ---> IM A NEWBIE, TAKE CARE <---

as well written in the linux nvidia driver readme (keep in mind: give always more than a look at readmes!!!) at this location for geforce/tnt2 cards 

[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7167/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7167/README.txt)

from the prompt (if doesnt work this way maybe u need to do that with root powers or sudo)
type the install utility with the uninstall option:

FEATURES OF NVIDIA-INSTALLER

o Uninstall: Driver installation will backup any conflicting files
  and record what new files are installed on the system.  You may run:

    nvidia-installer --uninstall
  
  to uninstall the current driver; this will remove any files that
  were installed on the system, and restore any backed up files.
  Installing new drivers implicitly uninstalls any previous drivers.

that should work any where u are in the tree of your drive, if not go to the dir where u downloaded the nvidia dirver and  inside the directory created by the installer (maybe a name similar to the installer itself) try repeat the cimmand.

i hope that can help u, byez

---

### Post by marcadams on 2005-03-15
Thanks iomicifikko;

I would love to get my Ubuntu box working again, so I'll try anything!

Thanks for your help
Marc

---

### Post by kamstrup on 2005-03-15
If I understood correctly, you where able to boot to a terminal prompt, right?

If you are in the terminal, do a "sudo nano -w /etc/X11/xorg.conf". Now find the "Device" section. Find the line that says

Driver "nvidia"

and change it to 

Driver "nv"

Save, and reboot.

Cheers

---

### Post by marcadams on 2005-03-15
Thanks for everyone's input !!

In the end I thought kamstrup's advice seemed the less distructive as an inital attempt, Once I had got the hang of Nano (and not saved the file in Mac format  :oops:  ), I rebooted my system and Yippee - it was all better!!

Thanks to everyone for their help ( especially kamstrup)


Howver, this does bring up one question - what driver am I now actually using? What is "nv"
Can I use the Nvidia settings GUI, or should I now just un-install the Nvidia driver and settings package?


Thanks again,
Marc

---

### Post by kamstrup on 2005-03-16
nv is the generic driver for cards based on the nvidia chipset. It will not give you 3d acceleration, but if you don't need that badly most people should be able to live with it. For me the biggest problem with the nv driver is that it wont give me refresh rates higher than 60Mhz when my screen is 1280x1024. Anything under 75MHz hurts my eyes. If I set my screen to 1024x720 nv gives me 75MHz though so, it's not totally bad :)

Now that you've learned to rescue yourself you can always try playing with the real nvidia driver...

Good luck

---

### Post by marcadams on 2005-03-16
hi kamstrup;

Thanks a lot. If "nv" is a generic driver, then I assume I can un-install the troublesome nvidia driver

I also assume, that the Nvidia settings package will not work with this generic driver?

Is that correct?


Thanks

---

### Post by kamstrup on 2005-03-16
[QUOTE=marcadams]hi kamstrup;

Thanks a lot. If "nv" is a generic driver, then I assume I can un-install the troublesome nvidia driver

I also assume, that the Nvidia settings package will not work with this generic driver?

Is that correct?


Thanks[/QUOTE]
 You are correct. The nvidia-settings package will not work for nv. To uninstall the nvidia drivers use Synaptic. You'll find it in the menu under System->Admin.->Synaptic. In Synaptic just search for "nvidia", to find the relevant packages.

---

### Post by marcadams on 2005-03-16
Hi kamstrup

Thanks for your help on this, I realy appreciate it.

I just wanted to make sure, if I uninstalled the nvidia packges, I would not effect my current set up.

Cheers
Marc

---

