---
title: "Dell Inspiron 15R Special Edition, and Ubuntu"
date: 2013-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by amjad-535 on 2013-11-07
I've decided to create this topic as a tutorial for those who want to install Ubuntu on Dell Inspiron 15R, and to find support for things that I still can't fix, and then update it for other users.

--- The tutorial part ---

To install Ubuntu, create your USB/CD using the Startup Disk Creator on another Ubuntu device.

Boot into the preinstalled Windows 8. Search for **Intel Storage**. Open the program and disable acceleration.

If you're using a USB, press **F2** as the laptop boots. Go to the boot menu and turn off the secure boot. Choose the **UEFI Secure Boot Off** option.

Boot into the Live USB/CD, open the terminal. Using **fdisk -l** (or GParted), identify your SSD. For example, **/dev/sda** or **/dev/sdb**

Using the terminal, type **sudo dmraid -E -r /dev/sdb** (or sda, if that was your case)

Run the installation, and it should go fine. You might have a problem where Ubuntu says that the resources are busy. Just keep trying, maybe change the Ext4 to Ext3, and it will work.

As you boot into Ubuntu, go to [http://support.amd.com/en-us/download/desktop?os=Linux+x86](http://support.amd.com/en-us/download/desktop?os=Linux+x86) and install the driver using the instructions at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Install the latest beta version because it supports 13.10. Run the file using **sudo sh amd-(filename I forgot).run --buildpkg Ubuntu/saucy**

Proceeding with hardware acceleration instructions caused problems here, but it looks like they already work.

--- Troubleshooting ---

- Brightness buttons don't work
Open the terminal and type **sudo nano /etc/default/grub**. Change the line **GRUB_CMDLINE_LINUX=""** to [B]GRUB_CMDLINE_LINUX="quiet splash acpi_osi=Linux acpi_backlight=vendor"
[/B]
- Touchpad lock while typing doesn't work
Here. [http://askubuntu.com/a/300879](http://askubuntu.com/a/300879)

--- The questions part ---

- The keyboard layout isn't perfect. The top left button for example is ` instead of <, and the bottom left button is < instead of \, plus one another button at the middle vertical right, very right, which is \ instead of `
- The dual monitor is glitched in an awful way. I can't see anything. A video is attached. There's no tab in the catalyst for monitors.
- Sometimes in Chromium the pages titles doesn't appear. A screenshot is attached. That only happens with Radeon drivers are activated.
- Ubuntu freezes (I have to reboot) (sometimes, not always) when system is locked (CTRL + ALT + L), when Radeon card is activated.

I hope someone can help with that. Thanks.

---

### Post by amjad-535 on 2013-11-08
Updated, fixed brightness.

---

### Post by amjad-535 on 2013-11-08
Question added. "System freezes on lock with AMD graphics enabled. Any fix for that?"

UPDATE

Looks like that happens at specific times. It works now, weird.

SECOND UPDATE:

Confirmed. Sometimes it crashes and other times not. Weird.

---

### Post by blortuga on 2013-11-22
I have a similar machine (15 SE; Inspiron 7520, with a Radeon HD 7700).
This somewhat relates, but otherwise, disregard this.

This machine has EFI with Legacy, and I was previously installed under legacy mode.
I finally got EFI mode to work, and re-installed to 13.10.

When I installed the Catalyst driver, I installed the 13.4 version (latest Release - as of this posting).
This failed to install, rendering gdm a "hot mess".

(I later, found that it did not support the kernel version in Ubuntu 13.10).

I installed the 13.11 beta 6 Catalyst driver.

When I rebooted, I still could not get a graphical session going. (blank black screen).  

I pressed ctrl-alt-F2, to get into a console login session. I ran the aticonfig --initial command, and this created a baseline aticonfig file for me.

The result was that I got into a graphical session, logged in, and saw that the Radeon HD 7700 was recognized.  But Unity crashed a bunch of times. (crash reporter said that it was fglrx, and x.org that crashed.  Each crashed multiple times right after I logged-in, but after that, the system seemed stable).

Every time I boot, and log-in, I get these crashes, but then I can go-on and continue working.

Power/heat seem to be pretty much on-par with the default install (using the discrete Intel graphics).  
Video quality seems better.
Boot time (time for the OS to load) is about 10-15 seconds longer though. Which is a shame because I was enjoying the MUCH faster boot-time with the transition from Legacy to UEFI.

---

### Post by blortuga on 2013-11-24
I just wanted to add:
exploring this 13.11 beta 6 driver further. . .  I found that it would always hang on suspend/resume.
I tried various settings in /etc/default/grub, (nomodeset made things much worse), and could not fix it.

So I went back to the open-source driver until Catalyst catches up with the newer kernel. :(

---

### Post by amjad-535 on 2013-12-06
> **blortuga said:**
> I just wanted to add:
exploring this 13.11 beta 6 driver further. . .  I found that it would always hang on suspend/resume.
I tried various settings in /etc/default/grub, (nomodeset made things much worse), and could not fix it.

So I went back to the open-source driver until Catalyst catches up with the newer kernel. :(

The open-source driver didn't work for me. Check out the new AMD driver. Run the aticonfig BEFORE rebooting. Also, use the option where packages are created. The other one sometimes fails.

---

