---
title: "Flashing wrongly sized destop after login"
date: 2021-01-17
forum: Desktop Environments
---

### Post by Pow_2k on 2021-01-17
After recent updates to one of my 20.04 desktops, on reboot the desktop became unusable.  I would login (tried both Gnome and Wayland) and the desktop would fail to properly load up.  At worst it might go to a solid color screen with mouse cursor available and then kick back to a login (possibly triggered by me via input, not 100% sure) and at best it would just flash the desktop in a zoomed out fashion and never be usable.  I have a sample of this on YouTube: [https://youtu.be/TAJLRMZeFew](https://youtu.be/TAJLRMZeFew)  I suspect this was a screen effect of the desktop zooming in to full size that just never completed.  I can still Ctrl+Alt+F3 to get to a terminal and that works properly.  I've rebooted into the other installed kernels available in grub and still have the issue, if I boot off of my 20.04 USB install stick the screen is fine.  Those lead me to believe that it is not hardware (stick works) and it is not kernel related (kernels I've used for months w/o issue now show problem).  This makes me think it is something either with the X.org server or with software that runs on desktop load, or a  recent display driver update if there was one.  Video would be on-board to the MB, Intel H87 chipset.

I'm thinking I could start with stopping software from loading on login but I've got no idea how to do so.  Non-OTB GUI items I've got that I can think of off the top of my head:
* Conky
* Screen sharing enabled
* Gnome System Monitor shell extension
* Solaar is installed and would often auto-display the GUI window on login

Below are packages showing in the dpkg.log installed prior to the reboot where the issue appeared, but it is possible something was installed earlier that wasn't fully in effect until this reboot.  I'd need to look at everything from December 20th to January 12th that got installed and it doesn't look like the dpkg.log goes back that far.
```
2021-01-05 06:21:35 status installed python3-apt:amd64 2.0.0ubuntu0.20.04.3
2021-01-05 06:21:38 status installed python-apt-common:all 2.0.0ubuntu0.20.04.3
2021-01-05 06:21:42 status installed libproxy1v5:amd64 0.4.15-10ubuntu1.2
2021-01-05 06:21:42 status installed libproxy1-plugin-networkmanager:amd64 0.4.15-10ubuntu1.2
2021-01-05 06:21:42 status installed libproxy1-plugin-gsettings:amd64 0.4.15-10ubuntu1.2
2021-01-05 06:21:42 status installed libc-bin:amd64 2.31-0ubuntu9.1
2021-01-05 15:48:12 status installed linux-modules-5.4.0-59-generic:amd64 5.4.0-59.65
2021-01-05 15:48:13 status installed linux-headers-5.4.0-59:all 5.4.0-59.65
2021-01-05 15:48:14 status installed linux-image-5.4.0-59-generic:amd64 5.4.0-59.65
2021-01-05 15:48:14 status installed linux-headers-5.4.0-59-generic:amd64 5.4.0-59.65
2021-01-05 15:48:15 status installed linux-modules-extra-5.4.0-59-generic:amd64 5.4.0-59.65
2021-01-05 15:48:15 status installed linux-headers-generic-hwe-20.04:amd64 5.4.0.59.62
2021-01-05 15:48:15 status installed linux-image-generic-hwe-20.04:amd64 5.4.0.59.62
2021-01-05 15:48:15 status installed linux-generic-hwe-20.04:amd64 5.4.0.59.62
2021-01-05 15:48:36 status installed linux-image-5.4.0-59-generic:amd64 5.4.0-59.65
2021-01-05 15:49:16 status installed nautilus-sendto:amd64 3.8.6-3ubuntu0.20.04.1
2021-01-05 15:50:09 status installed linux-firmware:all 1.187.7
2021-01-05 15:50:09 status installed libasound2-data:all 1.2.2-2.1ubuntu2.3
2021-01-05 15:50:09 status installed libasound2:amd64 1.2.2-2.1ubuntu2.3
2021-01-05 15:50:09 status installed libatopology2:amd64 1.2.2-2.1ubuntu2.3
2021-01-05 15:50:10 status installed man-db:amd64 2.9.1-1
2021-01-05 15:50:10 status installed libc-bin:amd64 2.31-0ubuntu9.1
2021-01-06 06:43:34 status installed linux-modules-extra-5.4.0-56-generic:amd64 5.4.0-56.62
2021-01-06 06:43:36 status installed linux-image-5.4.0-56-generic:amd64 5.4.0-56.62
2021-01-06 06:43:38 status installed linux-modules-5.4.0-56-generic:amd64 5.4.0-56.62
2021-01-06 06:43:42 status installed linux-headers-5.4.0-56-generic:amd64 5.4.0-56.62
2021-01-06 06:43:43 status installed linux-headers-5.4.0-56:all 5.4.0-56.62
2021-01-06 06:43:49 status installed libp11-kit0:amd64 0.23.20-1ubuntu0.1
2021-01-06 06:43:49 status installed p11-kit-modules:amd64 0.23.20-1ubuntu0.1
2021-01-06 06:43:49 status installed libc-bin:amd64 2.31-0ubuntu9.1
2021-01-06 06:43:54 status installed firefox-locale-en:amd64 84.0.1+build1-0ubuntu0.20.04.1
2021-01-06 06:43:59 status installed libopenexr24:amd64 2.3.0-6ubuntu0.3
2021-01-06 06:43:59 status installed libc-bin:amd64 2.31-0ubuntu9.1
2021-01-06 06:44:09 status installed firefox:amd64 84.0.1+build1-0ubuntu0.20.04.1
2021-01-06 06:44:10 status installed man-db:amd64 2.9.1-1
2021-01-06 06:44:10 status installed desktop-file-utils:amd64 0.24-1ubuntu3
2021-01-06 06:44:10 status installed mime-support:all 3.64ubuntu1
2021-01-06 06:44:10 status installed hicolor-icon-theme:all 0.17-2
2021-01-06 06:44:10 status installed gnome-menus:amd64 3.36.0-1ubuntu1
2021-01-06 06:44:15 status installed p11-kit:amd64 0.23.20-1ubuntu0.1
2021-01-06 06:44:17 status installed man-db:amd64 2.9.1-1
2021-01-07 06:26:10 status installed linux-hwe-5.8-headers-5.8.0-34:all 5.8.0-34.37~20.04.2
2021-01-07 06:26:10 status installed linux-headers-5.8.0-34-generic:amd64 5.8.0-34.37~20.04.2
2021-01-07 06:26:10 status installed linux-headers-generic-hwe-20.04:amd64 5.8.0.34.37~20.04.20
2021-01-07 06:26:14 status installed linux-modules-5.8.0-34-generic:amd64 5.8.0-34.37~20.04.2
2021-01-07 06:26:16 status installed linux-image-5.8.0-34-generic:amd64 5.8.0-34.37~20.04.2
2021-01-07 06:26:17 status installed linux-modules-extra-5.8.0-34-generic:amd64 5.8.0-34.37~20.04.2
2021-01-07 06:26:17 status installed linux-image-generic-hwe-20.04:amd64 5.8.0.34.37~20.04.20
2021-01-07 06:26:17 status installed linux-generic-hwe-20.04:amd64 5.8.0.34.37~20.04.20
2021-01-07 06:26:36 status installed linux-image-5.8.0-34-generic:amd64 5.8.0-34.37~20.04.2
2021-01-07 06:26:41 status installed libwavpack1:amd64 5.2.0-1ubuntu0.1
2021-01-07 06:26:41 status installed libc-bin:amd64 2.31-0ubuntu9.1
2021-01-09 06:24:48 status installed firefox:amd64 84.0.2+build1-0ubuntu0.20.04.1
2021-01-09 06:24:49 status installed man-db:amd64 2.9.1-1
2021-01-09 06:24:49 status installed desktop-file-utils:amd64 0.24-1ubuntu3
2021-01-09 06:24:49 status installed mime-support:all 3.64ubuntu1
2021-01-09 06:24:50 status installed hicolor-icon-theme:all 0.17-2
2021-01-09 06:24:50 status installed gnome-menus:amd64 3.36.0-1ubuntu1
2021-01-09 06:26:26 status installed linux-hwe-5.8-headers-5.8.0-36:all 5.8.0-36.40~20.04.1
2021-01-09 06:26:29 status installed linux-modules-5.8.0-36-generic:amd64 5.8.0-36.40~20.04.1
2021-01-09 06:26:29 status installed linux-headers-5.8.0-36-generic:amd64 5.8.0-36.40~20.04.1
2021-01-09 06:26:31 status installed linux-image-5.8.0-36-generic:amd64 5.8.0-36.40~20.04.1
2021-01-09 06:26:32 status installed linux-modules-extra-5.8.0-36-generic:amd64 5.8.0-36.40~20.04.1
2021-01-09 06:26:32 status installed linux-headers-generic-hwe-20.04:amd64 5.8.0.36.40~20.04.21
2021-01-09 06:26:32 status installed linux-image-generic-hwe-20.04:amd64 5.8.0.36.40~20.04.21
2021-01-09 06:26:32 status installed linux-generic-hwe-20.04:amd64 5.8.0.36.40~20.04.21
2021-01-09 06:26:51 status installed linux-image-5.8.0-36-generic:amd64 5.8.0-36.40~20.04.1
2021-01-09 06:27:03 status installed tzdata:all 2020f-0ubuntu0.20.04
2021-01-09 06:27:08 status installed firefox-locale-en:amd64 84.0.2+build1-0ubuntu0.20.04.1
2021-01-09 06:27:12 status installed libopenjp2-7:amd64 2.3.1-1ubuntu4.20.04.1
2021-01-09 06:27:12 status installed libc-bin:amd64 2.31-0ubuntu9.1
2021-01-10 06:32:15 status installed linux-headers-5.4.0-59-generic:amd64 5.4.0-59.65
2021-01-10 06:32:20 status installed linux-modules-extra-5.4.0-59-generic:amd64 5.4.0-59.65
2021-01-10 06:32:21 status installed linux-image-5.4.0-59-generic:amd64 5.4.0-59.65
2021-01-10 06:32:27 status installed linux-modules-5.4.0-59-generic:amd64 5.4.0-59.65
2021-01-10 06:32:31 status installed linux-headers-5.4.0-59:all 5.4.0-59.65
2021-01-12 06:54:40 status installed tzdata:all 2020f-0ubuntu0.20.04.1
2021-01-12 18:34:21 status installed libglvnd0:amd64 1.3.2-1~ubuntu0.20.04.1
2021-01-12 18:34:22 status installed update-notifier-common:all 3.192.30.3
2021-01-12 18:34:22 status installed libllvm11:amd64 1:11.0.0-2~ubuntu20.04.1
2021-01-12 18:34:22 status installed libgles2:amd64 1.3.2-1~ubuntu0.20.04.1
2021-01-12 18:34:22 status installed libglapi-mesa:amd64 20.2.6-0ubuntu0.20.04.1
2021-01-12 18:34:22 status installed xserver-common:all 2:1.20.9-2ubuntu1.1~20.04.1
2021-01-12 18:34:22 status installed libdrm-common:all 2.4.102-1ubuntu1~20.04.1
2021-01-12 18:34:23 status installed xserver-xorg-legacy:amd64 2:1.20.9-2ubuntu1.1~20.04.1
2021-01-12 18:34:23 status installed libdrm2:amd64 2.4.102-1ubuntu1~20.04.1
2021-01-12 18:34:23 status installed libdrm-amdgpu1:amd64 2.4.102-1ubuntu1~20.04.1
2021-01-12 18:34:23 status installed mesa-vulkan-drivers:amd64 20.2.6-0ubuntu0.20.04.1
2021-01-12 18:34:23 status installed libdrm-nouveau2:amd64 2.4.102-1ubuntu1~20.04.1
2021-01-12 18:34:23 status installed libgbm1:amd64 20.2.6-0ubuntu0.20.04.1
2021-01-12 18:34:23 status installed libdrm-radeon1:amd64 2.4.102-1ubuntu1~20.04.1
2021-01-12 18:34:23 status installed libdrm-intel1:amd64 2.4.102-1ubuntu1~20.04.1
2021-01-12 18:34:23 status installed libgl1-mesa-dri:amd64 20.2.6-0ubuntu0.20.04.1
2021-01-12 18:34:23 status installed libxatracker2:amd64 20.2.6-0ubuntu0.20.04.1
2021-01-12 18:34:23 status installed libegl-mesa0:amd64 20.2.6-0ubuntu0.20.04.1
2021-01-12 18:34:23 status installed libegl1:amd64 1.3.2-1~ubuntu0.20.04.1
2021-01-12 18:34:23 status installed mesa-va-drivers:amd64 20.2.6-0ubuntu0.20.04.1
2021-01-12 18:34:23 status installed mesa-vdpau-drivers:amd64 20.2.6-0ubuntu0.20.04.1
2021-01-12 18:34:23 status installed libglx-mesa0:amd64 20.2.6-0ubuntu0.20.04.1
2021-01-12 18:34:23 status installed libglx0:amd64 1.3.2-1~ubuntu0.20.04.1
2021-01-12 18:34:23 status installed libgl1:amd64 1.3.2-1~ubuntu0.20.04.1
2021-01-12 18:34:23 status installed xserver-xephyr:amd64 2:1.20.9-2ubuntu1.1~20.04.1
2021-01-12 18:34:23 status installed xwayland:amd64 2:1.20.9-2ubuntu1.1~20.04.1
2021-01-12 18:34:23 status installed xserver-xorg-core:amd64 2:1.20.9-2ubuntu1.1~20.04.1
2021-01-12 18:34:23 status installed hicolor-icon-theme:all 0.17-2
2021-01-12 18:34:23 status installed update-notifier:amd64 3.192.30.3
2021-01-12 18:34:23 status installed libglib2.0-0:amd64 2.64.3-1~ubuntu20.04.1
2021-01-12 18:34:23 status installed libc-bin:amd64 2.31-0ubuntu9.1
2021-01-12 18:34:26 status installed man-db:amd64 2.9.1-1
2021-01-12 18:47:45 status installed lsof:amd64 4.93.2+dfsg-1ubuntu0.20.04.1
2021-01-12 18:47:45 status installed xdg-utils:all 1.1.3-2ubuntu1.20.04.2
2021-01-12 18:47:45 status installed desktop-file-utils:amd64 0.24-1ubuntu3
2021-01-12 18:47:45 status installed mime-support:all 3.64ubuntu1
2021-01-12 18:47:45 status installed gnome-menus:amd64 3.36.0-1ubuntu1
2021-01-12 18:47:45 status installed mutter-common:all 3.36.7+git20201123-0.20.04.1
2021-01-12 18:47:45 status installed libglib2.0-0:amd64 2.64.3-1~ubuntu20.04.1
2021-01-12 18:47:45 status installed libc-bin:amd64 2.31-0ubuntu9.1
2021-01-12 18:47:47 status installed man-db:amd64 2.9.1-1
2021-01-12 18:47:48 status installed libmutter-6-0:amd64 3.36.7+git20201123-0.20.04.1
2021-01-12 18:47:48 status installed gir1.2-mutter-6:amd64 3.36.7+git20201123-0.20.04.1
2021-01-12 18:47:48 status installed mutter:amd64 3.36.7+git20201123-0.20.04.1
2021-01-12 18:47:48 status installed libc-bin:amd64 2.31-0ubuntu9.1
2021-01-12 19:11:14 status installed libgcc1:amd64 1:10.2.0-5ubuntu1~20.04
2021-01-12 19:11:14 status installed libc-bin:amd64 2.31-0ubuntu9.1
2021-01-12 19:11:23 status installed libllvm10:amd64 1:10.0.0-4ubuntu1
2021-01-12 19:11:23 status installed libc-bin:amd64 2.31-0ubuntu9.1

```

This is my first time running into this sort of a problem with Ubuntu and I'm not sure of the next steps to take.  Any suggestions?

---

### Post by Bashing-om on 2021-01-17
Pow_2kPow_2k; Hello -

How about this for a thought -
Broken graphic's driver.

What have we for:
```

sudo lshw -C display

```

 Nvidia/AMD chipsets ? No driver - then we can poke at it some more with the "nomodeset" boot parameter for a confirmation of driver issues.

[INDENT][INDENT]there is a process
[/INDENT][/INDENT]

---

### Post by Pow_2k on 2021-01-17
Here's the sudo lshw -C display ouput:```

  *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff
```

---

### Post by Bashing-om on 2021-01-17
Pow_2k; Welp -

So much for that thought -
Intel; and Intel "just works" - the driver is included in the kernel and the i915 driver is available.

Presently I have no other suggestion to offer.

[INDENT]A know-it-all I am not
[/INDENT]

---

### Post by Pow_2k on 2021-01-17
Thanks for the try.  It's early on, hopefully someone else will come along with additional insight!

---

### Post by Bashing-om on 2021-01-17
> **Pow_2k said:**
> Thanks for the try.  It's early on, hopefully someone else will come along with additional insight!

+10

There is a world of knowledge here

---

### Post by &amp;KyT$0P# on 2021-01-17
Do you have a specific reason you need the HWE (5.8) kernel in this 20.04 install?
Does the problem occur if you boot this 20.04 install with the latest 5.4 kernel you have installed?

---

### Post by Pow_2k on 2021-01-17
> **halogen2 said:**
> Do you have a specific reason you need the HWE (5.8) kernel in this 20.04 install?
Does the problem occur if you boot this 20.04 install with the latest 5.4 kernel you have installed?
No specific reason for 5.8 that I'm aware of, just running the updates as they're available.

I'm sure I tried booting from all the available kernels in grub previously with no luck.  But I went and looked this time and only 5.8 kernels were listed.  I reinstalled a 5.4 kernel, rebooted, selected it from grub, and DING!  Success!  Usable desktop again.

So, what am I advised to do from here?  Since future updates will just purge off old kernels I need to avoid those for the time being.  Hopefully this is already being looked at and will be corrected in the 5.8 kernel.

---

### Post by Pow_2k on 2021-01-18
Based on reading [this Ask Ubuntu entry]("https://askubuntu.com/questions/1288395/system-is-unusable-after-upgrade-to-20-10-i915-gpu-hang") I'm going to guess what I'm experiencing is related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1872001").

---

### Post by &amp;KyT$0P# on 2021-01-18
> **Pow_2k said:**
> No specific reason for 5.8 that I'm aware of, just running the updates as they're available.

I'm sure I tried booting from all the available kernels in grub previously with no luck.  But I went and looked this time and only 5.8 kernels were listed.  I reinstalled a 5.4 kernel, rebooted, selected it from grub, and DING!  Success!  Usable desktop again.

So, what am I advised to do from here? 

My suggestion would be you adjust which kernel metapackages you have installed, such that you only get the latest 5.4.x kernel.  Step 1 is to install that metapackage -
```
sudo apt-get install linux-generic
```

Then reboot into latest installed 5.4.x kernel and purge the problematic 5.8 kernels & HWE kernel metapackages.

---

