---
title: "Can't figure out how to make Ubuntu 16.04 utilize my Nvidia graphics card :("
date: 2016-07-22
forum: Gaming &amp; Leisure
---

### Post by snaysler on 2016-07-22
[tl;dr below]

Hi guys, brand new to this forum, brand new to linux (Ubuntu 16.04), brand new to the tremendous tediousness of making things do what you want them to do outside of Windows 10 lol. I'd really appreciate some technical help here.

I got PlayOnLinux, and successfully installed League of Legends. Took about 10 times longer to load the game up than with Windows 10, then when it finally ran it was clearly rendering graphics with my CPU. About 0.5 frames per second, and I have a Intel® Core&#8482; i7-4980HQ CPU! He's a fast little guy but he can't do what my GPU can do. I have an Nvidia Geforce GTX 980M. I've read several guides on the internet about how to install nvidia drivers (all completely different) and nothing has worked clearly. One of them used something called bumblebee (made my computer unable to log in), one installed driver using apt-get with a simple command, one required all these file modifications etc etc. Clearly nothing's worked.

tl;dr-
I have an MSI gt72 dominator laptop
I am running Ubuntu 16.04
Intel® Core&#8482; i7-4980HQ
Nvidia Geforce GTX 980M
How do I get Nvidia drivers working??

Really appreciate any help guys, thanks in advance!

---

### Post by oldfred on 2016-07-22
Bumblebee has been depreciated in favor of nvidia-prime 

And what video driver did you install, and how, from repository, nVidia or ppa?

      
 remove bumblebee
[http://ubuntuforums.org/showthread.php?t=2292628](http://ubuntuforums.org/showthread.php?t=2292628)
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms 

And installing a new nVidia driver can create conflicts as old is not automatically uninstalled.
      
 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended  
   sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall 

If listed driver is not new enough for your video card, you can add the ppa.
      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[URL="https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"]https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa

[/URL]
 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices 

Even newer nVidia card. Booted with Intel graphics, then installed nVidia driver.
[https://ubuntuforums.org/showthread.php?t=2327648](https://ubuntuforums.org/showthread.php?t=2327648)

[URL="https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"]
[/URL]

---

### Post by snaysler on 2016-07-22
I have tried:
sudo apt-get install nvidia-340
sudo apt-get install nvidia-361
sudo apt-get install nvidia-367

I have tried going to "Software and Updates" -> "Additional Drivers", then selected the radiobutton saying "Using NVIDIA binary driver - version 361.42 from nvidia-361 (proprietary, tested)".

I have tried downloading the ".run" file from the nVidia website and running that which at first said I was running an x server, which i figured out how to stop (something with 'lightdm' service) and then I'd try installing it, but my computer wouldn't allow me to log in or get past login screen.

Just got this feedback

> 
snaysler@tayler-ubuntu:~$ ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free


== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
model    : GM204M [GeForce GTX 980M]
modalias : pci:v000010DEd000013D7sv00001462sd00001129bc03sc00i00
vendor   : NVIDIA Corporation
driver   : nvidia-361 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin




> **oldfred said:**
> Bumblebee has been depreciated in favor of nvidia-prime 

And what video driver did you install, and how, from repository, nVidia or ppa?

      
 remove bumblebee
[http://ubuntuforums.org/showthread.php?t=2292628](http://ubuntuforums.org/showthread.php?t=2292628)
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms 

And installing a new nVidia driver can create conflicts as old is not automatically uninstalled.
      
 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended  
   sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall 

If listed driver is not new enough for your video card, you can add the ppa.
      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[URL="https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"]https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa

[/URL]
 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices 

Even newer nVidia card. Booted with Intel graphics, then installed nVidia driver.
[https://ubuntuforums.org/showthread.php?t=2327648](https://ubuntuforums.org/showthread.php?t=2327648)

[URL="https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"]
[/URL]

---

### Post by oldfred on 2016-07-22
It sounds like you have installed way too many versions of nVidia. Each will conflict.
You need to purge and reinstall just one.
Do not use the .run from nVidia, a ppa can give you the very newest if needed. And the .run file requires reconfiguration on every kernel update as it is not fully implemented in Ubuntu.

If boot issues, often nomodeset puts you in a low quality graphics mode until you get nVidia installed.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset. 
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by snaysler on 2016-07-23
I totally got it working, thanks my man. That ppa thing was the trick after purging.

---

### Post by oldrocker99 on 2016-07-24
Please mark your thread as [SOLVED].

---

