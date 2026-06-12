---
title: "NVidia Driver doesn't work.... another novice!"
date: 2009-05-02
forum: General Help
---

### Post by NayC on 2009-05-02
Hi, I made a post here which has information about what i have done:

[http://ubuntuforums.org/showthread.php?t=1146349](http://ubuntuforums.org/showthread.php?t=1146349)

Basically, my installing either th latest nvidia "180" or older "173" driver causes my computer to break...

For the 3rd going on 4th re-install, I use the ubuntu cd (9.04, 32bit) and install ubuntu to a 30GB folder through windows. This is fine. It allows me to reboot and select either OS on install, which is through the GRUB boot loader yes? Well, I select ubuntu, which then happily goes through and finishes the install. The OS loads fine. Rebooting is fine, installing updates then rebooting is fine. Then trying to install the gpu drivers (either 96, 173 or 180) is where my problem lies...

It installs the drivers fine, but on reboot it puts me into a command line interface in which I can login, but have no access back into the GUI. I did a search somewhere and it said type "startx" in the command line to re-enter the GUI, if thats the wrong thing please let me know.

Now, I have a pc with a core i7 920, 6GB of 1866mhz Ram, and 2x 8800GTX gpu's. Currently the 2 gpus are plugged in, but with no sli bridge (had some issues a while back to tinker with, so required removing the connection and as of yet haven't been bothered to re-link them as I haven't had a need). Could this be a problem. Should i either link them together or remove one? Or would this not be the cause? Is ubuntu perfectly fine with i7 machines and far too much ram for the OS to even handle? This has been annoying me all day as I really want to play around with ubuntu properly.

Now, does anyone have any ideas? Or can someone please tell me if and when I get these driver problems, how to return to the standard drivers in the command line interface when I get stuck there... I know of "sudo apt-get autoremove nvidia-(version number)-modaliases" to remove the driver... but I still cant do anything once i have done that... 

Any help greatfully appriciated! Cheers, Nay.

---

### Post by 4Orbs on 2009-05-02
If you used wubi to install Ubuntu, then Ubuntu is actually installed inside a virtual machine on Windows.

My limited experience with virtual machines may cause me to assume this incorrectly. When I was using Ubuntu in VirtualBox, I was unable to install the nVidia driver .run package. I think this is because nVidia needs direct access to the hardware for a successful compilation and installation of the driver, but the virtual machine blocks any direct access. I would guess that the Hardware Drivers Mgr might be the best and maybe only way to have a working driver in a virtual machine. Someone please scold me if I'm wrong.

---

### Post by NayC on 2009-05-02
Thanks!

I know that the drivers dont work in a virtual machine but i didn't know wubi did that..(yes thats how i installed ubuntu!)

Through VMWare, it was much more along the lines of failing on the install rather than complete the install then fail on reboot.

How should I go about installing ubuntu directly then? If all my HDDs are already patitioned in windows? Will I have to use a partition manager and somehow create one, and boot via the ubuntu disk? If so, what is the best program to use and a little advise might be nice!

I have plenty of space left on the drive I wish to install ubunutu on (well the vm was 30GB on my 500GB C:, which has well over 200GB free). Would this be able to be partitioned to say break 100GBs off it to make a linux partition?

---

### Post by 4Orbs on 2009-05-02
There are oodles of tutorials for different ways to install Ubuntu and dual-boot (or multiple-boot if you like over-doing things) with Windows.

Personally, for partitioning schemes, I keep Ubuntu on the HDD right next to the Windows partition. Ubuntu is on a relatively small space (60GB or less), and I have my second HDD as one large common storage (NTFS) partition that can be shared between Windows and Ubuntu.

The Ubuntu live install disc has the partitioner included and is easy and straightforward to use. I suggest you choose the manual option for partitioning the HDDs to your exact preferences.

---

### Post by NayC on 2009-05-02
I know it comes with Wubi, but thats making a Virtual Drive inside windows, which is making my graphics drivers fail.

Is there a way to properly partition an existing windows drive with masses of space still free? (still 250GB+).

---

### Post by 4Orbs on 2009-05-02
Do you have the most recent Ubuntu live cd? If so, you need to set your computer BIOS to boot first from cd, then you can install it directly to HDD partitions rather than usin wubi.

I suggest doing some reading over at [Psychocats Tutorials]("http://www.psychocats.net/") while you're waiting for the Ubuntu cd download to complete. Psychocats covers all you need to know for a delightful Ubuntu installation.

---

### Post by NayC on 2009-05-02
Thanks 4Orbs, I will read that. Either way, I do have the latest CD (9.04) and I have used vista's disk management to shrink 50GB's off my C: which should allow me to install a clean ubuntu.

Hopefully, that will install ubuntu fine and allow me to install the latest drivers etc...

Pray this works.

---

### Post by 4Orbs on 2009-05-02
I'll bet you repartition and re-install Ubuntu (and others) frequently, just because it's so much fun. Seriously.

---

### Post by NayC on 2009-05-02
Haha, great fun! (I just want it work :( ) 
 
Well, I've repartitioned it, got it installed and suprise, suprise the same problem?? 
 
Does anyone have a reason why this may happen?

---

### Post by 4Orbs on 2009-05-02
Did you manually install the .run package from nvidia's website, or use the Hardware Drivers Mgr version?

---

### Post by ed-koala on 2009-05-02
I know exactly how to fix you up.  The problem is in the dual graphics card. Here's the solution:

First, open Synaptic and make sure the following pkgs are installed:

make
gcc
build-essential
dkms
linux-headers-2.6.27-9 (assumes you use the current kernel)
linux-headers-2.6.27-9-generic
linux-generic
linux-headers-generic
module-assistant

Next, make sure the following are NOT installed, and use the "Mark for complete removal option" if any need to be removed:

ALL nvidia pkgs (search for nvidia)
Any old kernel pkgs, ie linux-headers-2.6.27-7 and earlier, etc
(This might not be necessary, but I did it anyway)


Now, perform the following command in a terminal:

```
sudo lspci | grep VGA
```

The output will look something like this:

```

02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)

```

Write down the number begining each line.

Go to System-Administration-Hardware Drivers and choose 180.44 and activate the driver - DO NOT REBOOT yet!!!

*<If you have nothing to activate in hardware drivers, then go to Synaptic and install:>*

nvidia-180-libvdpau
nvidia-180-kernel source
nvidia-settings
nvidia-common

Open terminal and type:

```
sudo gedit /etc/X11/xorg.conf
```

Replace the graphics "Device" section with the following:

```

Section "Device"
Identifier "Configured Video Device"
BusID "PCI:**1**:0:0"
Driver "nvidia"
EndSection

```

Edit the BusID line to reflect the number you wrote down earlier (for me, that would be "PCI:2:0:0". *****MAKE SURE***** you use all colons as shown, and add the PCI part as shown.

If you have sli, add the following:

```
Option "sli" "auto"
```

Save the file, reboot and you should have 3d graphics working.
**Note** - for dual graphics PCs, you may boot to a black screen but you'll hear the normal boot sounds. If that happens, you used the wrong number in BusID. Change it to the other number OR plug your monitor into the other card.

---

### Post by NayC on 2009-05-02
Hardware Drivers Mgr version. Why, should I have done it differently?

Do you have any idea how I could restore this from the command prompt? To save me re-installing?

---

### Post by ed-koala on 2009-05-02
Yes, just purge the nvidia files and your system will do a basic boot. The command is:

```
sudo apt-get remove --purge nvidia*
```

Reboot and you should get in with basic graphics then you can apply the fix.

---

### Post by NayC on 2009-05-03
Harware Managers one. Last time I tried direct from the manu it just didn't work. Downloaded the file (well, it just opened a page with a hell of a lot of text) then told me to run it from the terminal. The errors were saying it couldnt run the file. I'll try again.

---

### Post by 4Orbs on 2009-05-03
When you download the .run file from nVidia's website, don't double click the file. Instead, right click on it and select "save link as" to your desktop.

The Hardware Drivers Mgr is better because once the driver is installed and activated, you never need to mess with it again. But with the manually installed driver from the .run package, you have to re-install it every time Ubuntu does a kernel update.

The Hardware Drivers Mgr is a little quirky at the moment. The progress bar doesn't move until the driver is almost finished installing. Then the progress bar will suddenly jump from 0% to 80% and complete the driver installation. Just wait a while after clicking the Activate Driver button.

---

### Post by NayC on 2009-05-03
[LEFT][FONT=Arial][SIZE=2]THANK YOU SO MUCH [/SIZE][/FONT]_[FONT=Arial][SIZE=2]Ed-Koala![/SIZE][/FONT]_
_[FONT=Arial][SIZE=2] [/SIZE][/FONT]_
_[FONT=Arial][SIZE=2] It was the dual GPUs. I have just removed one and bingo it runs fine.[/SIZE][/FONT]_
_[FONT=Arial][SIZE=2] [/SIZE][/FONT]_
[U][FONT=Arial][SIZE=2] Can I now do all the updating of the files now to be able to handle my second GPU, now that I'm back into the GUI?

(sorry its decided that it want to underline all my text!)
[/SIZE][/FONT][/U][/LEFT]
_[FONT=Arial][SIZE=2][/SIZE][/FONT]_

---

### Post by NayC on 2009-05-12
Thanks again Ed-Koala! Have followed your steps and have dual GPU's running fine!

---

