---
title: "Linux not booting on new hardware"
date: 2012-04-07
forum: Desktop Environments
---

### Post by HowUpDoHighKnee on 2012-04-07
Hello all,

I just bought a new Desktop PC with
[LIST]
[*]ASUS Sabertooth 990FX
[*]Zotac NVIDIA GTX 560 Ti
[*]AMD Penom X6 1100T
[/LIST]

Unfortuanly I can't boot any distro!
I tried many different Ubuntu, Knoppix, Fedora and Sabayon distros.
Nothing worked. Sometimes I get an bootup screen but stops with different errors.

I found an Ubuntu 9.04 Stick an tried this one and it worked, what really surprised me! It hasn't got the full 1080p display resolution but everything worked.

Does anybody experienced the same problems on similar hardware and/or has a trick?

---

### Post by Basher101 on 2012-04-07
cant you boot the Live CD or 
when you installed it on the disk you cant boot the full installed OS?

---

### Post by HowUpDoHighKnee on 2012-04-07
I can only boot the old Ubuntu 9.04 Stick.
Current Fedora CD/DVD and other Live Distros like Ubuntu 11.10 and 12.04 did not boot

---

### Post by Basher101 on 2012-04-07
so the Live CDs do not boot?

---

### Post by oldfred on 2012-04-07
I have an older nVidia card and for every recent version (since 9.10?) I have had to use nomodeset on liveCD or USB and on first boot until I install the nVidia drivers.

 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by HowUpDoHighKnee on 2012-04-07
It works!
Thank you all!
Just set "nomodeset" on boot and it starts in VESA mode limited to 1280 x 1024 pixel. will now try to install the nvidia drivers and try again.

---

### Post by Basher101 on 2012-04-07
i use a gtx 570 and had no boot problems at all. Never thought it was the video mode that kept you from booting. Anyways glad it finally works for you :popcorn:

---

### Post by HowUpDoHighKnee on 2012-04-07
bad news!

I restarted the fresh install but just getting a purple blank screen :(
Neither works with Ubuntu 11.10 nor 12.04

---

### Post by Basher101 on 2012-04-07
i get the blank purple on startup too, but it gets past that. You will probably need to enter the recovery mode and install the drivers with the command line

---

### Post by HowUpDoHighKnee on 2012-04-07
It's a strange problem...
Why does a old (Ubuntu 9.04) Version is working, the latest Ubuntu (12.04 beta/11.10) not?

Could it be the Motherboard?

If it's only the graphic card, this could be fixed with a new version of X-Server containing a newer nouveau driver or the full release of Ubuntu 12.04... 18 days left :)

Currently it's only working if I start with nomodeset or through the recovery menu with "low graphics"

---

### Post by Basher101 on 2012-04-07
hmm it is not the board, i can tell for sure. It is more of a kernel issue. I got some backlight problems on my laptop with 11.04 and onwards, which did not appear with 10.10. If you have to use nomodeset all the time, you should edit your grub configuration file so you must not apply it manually every time. 

This should work for you temporarily to at least use the system somehow....(i had the luck with my custom built desktop i made that everything worked)

To change it type in the terminal ```
gksu gedit /etc/default/grub
``` and edit the line that says ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` and edit it to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
``` save the file and then run the command ```
sudo update-grub
``` for the changes to take effect.

Reboot and see if it works

---

### Post by HowUpDoHighKnee on 2012-04-08
Thanks for the advice, but for those who are using grub2 (like me) you have to edit /etc/grub.d/00_header

If I install the display driver from nvidia.com the system just showing blank screen. May be because of a conflict between the nouveau and the nvidia driver!

I just installed the the nvidia-current package but with no effect :(

Hope 12.04 will fix this issue!

EDIT: I'll post the result of 12.04 final release test here!

---

