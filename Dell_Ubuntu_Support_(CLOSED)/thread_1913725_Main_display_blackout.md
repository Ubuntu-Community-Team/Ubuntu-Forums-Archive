---
title: "Main display blackout"
date: 2012-01-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bram Gadeyne on 2012-01-23
Hi,

I'm using ubuntu 11.10 (64 bit) on a Dell Latitude E5410.

Since yesterday my main display is blacked out. My External display however does function correctly.

Rebooting the system, disconnecting the external display and changing the preferences in the display preferences doesn't change anything.

What can I do next?

Kind regards Bram

---

### Post by Bram Gadeyne on 2012-01-23
Maybe also worth noting. I remember there were some updates the day before including some kernel update.

---

### Post by lepi_jr on 2012-01-24
I have the same problem.
This happened after ubuntu update

---

### Post by Bram Gadeyne on 2012-01-24
This issue was resolved by executing the recovery mode for ubuntu (the second line in te grup bootloader).

I just choose, resume normal reboot and my display worked again.

Kind regards
Bram

---

### Post by Bram Gadeyne on 2012-01-25
Hmm, Seems like the issue is still not solved. I can however startup using the recovery mode.

Some more info:

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

$ dmesg | grep intel
[    1.613750] intel_idle: MWAIT substates: 0x1120
[    1.613752] intel_idle: v0.4 model 0x25
[    1.613753] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.616152] ACPI: acpi_idle yielding to intel_idle
[    1.835875] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.836033] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.836890] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.837109] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   11.056747] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   11.056763] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   11.056803] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   11.059708] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   16.254663] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo



$ dmesg | grep graphic
[    1.517638] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[   11.056803] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   16.584176] init: udev-fallback-graphics main process (1104) terminated with status 1

---

### Post by paulodeleo on 2012-02-02
Got the same problem here, with exactly the same hardware.

I was using it just fine, with my primary display set to the external, plugged in by VGA and the laptop display as secondary, in extended mode.

There was a reboot request pending for some days, due to updates. After I finally rebooted, I can now only use my external display.

Tried to mess with ~/.config/monitor.xml, and even delete it and recreating it by just using the display manager, but nothing changes. Even changing to text mode by ctrl+alt+F1 doesn't work.

I do not have an /etc/X11/xorg.conf file.

The secondary display (in ubuntu) is active, when I take a screenshot, both screens are captured in the screen. 

I can control the brightness of the laptop screen, but it keeps at blank screen, even when booting. In fact, I can't even get the grub menu to show up, being able only to see the purple background with white small garbled dots.

What could break the display config at the level of the grub menu?

Is there any way to force the setup of the primary display?

---

### Post by Bram Gadeyne on 2012-02-03
I'm still having the same problem. The only thing that Works for me is booting in the recovery mode. But then ubuntu uses some generic driver and I can't use my secondary display.

---

### Post by paulodeleo on 2012-02-03
How do you enter recovery mode? I can't even see the grub menu, or blindly choose any option from it.

---

### Post by Bram Gadeyne on 2012-02-03
> **paulodeleo said:**
> How do you enter recovery mode? I can't even see the grub menu, or blindly choose any option from it.

I have a dual boot with Windows. When I reboot from ubuntu then my screen also remains blank after reboot.

When I reboot from Windows then my screen is OK again.

When I manually power off my laptop (pressing the power button long) then I can also see the grub bootloader on the next boot.

So it seems like it is some setting at hardware level that is changed by ubuntu and a forced power off resets it.

---

### Post by paulodeleo on 2012-02-03
I see. I don't have dual boot, so no default grub menu is shown.
But I could replicate something related to doing a cold boot. Then I try to access grub by holding the shift key on cold boot, sometimes I can see some characters.

They messed up the kernel or something like this to break video this way???

---

### Post by Bram Gadeyne on 2012-02-03
Someone on the #ubuntu channel on freenode someone told me to use add the nomodeset property in the boatloader.

ubuntuforums.org/showthread.php?t=1613132

I found out that this property is set for the recovery line two.

This however loads the generic display driver. So when booted I can't add a secondary display using this property.

There is however another option vt.handoff=7. This also has something to do with the display.

Maybe turning this off will help.

---

### Post by Bram Gadeyne on 2012-02-03
> **Bram Gadeyne said:**
> Someone on the #ubuntu channel on freenode someone told me to use add the nomodeset property in the boatloader.

ubuntuforums.org/showthread.php?t=1613132

I found out that this property is set for the recovery line two.

This however loads the generic display driver. So when booted I can't add a secondary display using this property.

There is however another option vt.handoff=7. This also has something to do with the display.

Maybe turning this off will help.

This didn' work either

---

### Post by paulodeleo on 2012-02-06
One thing I noticed is that after the problem started, now when I change to text mode (ctrl+alt+F1) this error message is shown several times, even before login:

> [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting

Can see them with "dmesg | grep -i intel" command too.

A google search about it shows some results about a bug somewhat similar, related to external displays, and still unsolved:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/749817](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/749817)

EDIT:

Found some [instructions to try to find what was updated]("http://ubuntuforums.org/showpost.php?p=10648987&postcount=3") and caused the problem. Seems like the recent updates are logged at /var/log/dpkg.log and can bee seen as:

> $ cat /var/log/dpkg.log | egrep 'install |upgrade '
2012-02-02 17:07:12 upgrade ifupdown 0.7~alpha5.1ubuntu5 0.7~alpha5.1ubuntu5.1
2012-02-02 17:07:13 upgrade accountsservice 0.6.14-1git1ubuntu1 0.6.14-1git1ubuntu1.1
2012-02-02 17:07:16 upgrade libaccountsservice0 0.6.14-1git1ubuntu1 0.6.14-1git1ubuntu1.1
2012-02-02 17:07:18 upgrade evince 3.2.1-0ubuntu2.1 3.2.1-0ubuntu2.2
2012-02-02 17:07:19 upgrade libevince3-3 3.2.1-0ubuntu2.1 3.2.1-0ubuntu2.2
2012-02-02 17:07:20 upgrade evince-common 3.2.1-0ubuntu2.1 3.2.1-0ubuntu2.2
2012-02-02 17:07:28 upgrade libgs9 9.04~dfsg-0ubuntu11.4 9.04~dfsg-0ubuntu11.5
2012-02-02 17:07:29 upgrade libgs9-common 9.04~dfsg-0ubuntu11.4 9.04~dfsg-0ubuntu11.5
2012-02-02 17:07:31 upgrade ghostscript 9.04~dfsg-0ubuntu11.4 9.04~dfsg-0ubuntu11.5
2012-02-02 17:07:32 upgrade ghostscript-x 9.04~dfsg-0ubuntu11.4 9.04~dfsg-0ubuntu11.5
2012-02-02 17:07:33 upgrade ghostscript-cups 9.04~dfsg-0ubuntu11.4 9.04~dfsg-0ubuntu11.5
2012-02-02 17:07:34 upgrade libicu44 4.4.2-2 4.4.2-2ubuntu0.11.10.1
2012-02-02 17:07:41 upgrade metacity-common 1:2.34.1-1ubuntu4 1:2.34.1-1ubuntu4.1
2012-02-02 17:07:43 upgrade libmetacity-private0 1:2.34.1-1ubuntu4 1:2.34.1-1ubuntu4.1
2012-02-02 17:07:43 upgrade libnux-1.0-0 1.16.0-0ubuntu1 1.16.0-0ubuntu1.1
2012-02-02 17:07:44 upgrade libnux-1.0-common 1.16.0-0ubuntu1 1.16.0-0ubuntu1.1
[B]2012-02-02 17:07:46 upgrade libunity-core-4.0-4 4.24.0-0ubuntu2.1 4.28.0-0ubuntu2
2012-02-02 17:07:47 upgrade unity-services 4.24.0-0ubuntu2.1 4.28.0-0ubuntu2[/B]
2012-02-02 17:07:48 upgrade libusbmuxd1 1.0.7-1 1.0.7-1ubuntu0.11.10.1
2012-02-02 17:07:49 upgrade metacity 1:2.34.1-1ubuntu4 1:2.34.1-1ubuntu4.1
2012-02-02 17:07:50 upgrade nux-tools 1.16.0-0ubuntu1 1.16.0-0ubuntu1.1
2012-02-02 17:07:51 upgrade python-software-properties 0.81.13.1 0.81.13.3
2012-02-02 17:07:52 upgrade software-properties-common 0.81.13.1 0.81.13.3
2012-02-02 17:07:53 upgrade software-properties-gtk 0.81.13.1 0.81.13.3
[B]2012-02-02 17:07:55 upgrade unity 4.24.0-0ubuntu2.1 4.28.0-0ubuntu2
2012-02-02 17:07:56 upgrade unity-common 4.24.0-0ubuntu2.1 4.28.0-0ubuntu2[/B]
2012-02-02 17:07:58 upgrade update-notifier 0.117ubuntu3.1 0.117ubuntu3.2
2012-02-02 17:07:59 upgrade update-notifier-common 0.117ubuntu3.1 0.117ubuntu3.2
2012-02-02 17:08:01 upgrade usbmuxd 1.0.7-1 1.0.7-1ubuntu0.11.10.1
[B]2012-02-02 17:08:03 upgrade x11-common 1:7.6+7ubuntu7 1:7.6+7ubuntu7.1
2012-02-02 17:08:06 upgrade xserver-xorg-video-all 1:7.6+7ubuntu7 1:7.6+7ubuntu7.1
2012-02-02 17:08:06 upgrade xserver-xorg-input-all 1:7.6+7ubuntu7 1:7.6+7ubuntu7.1
2012-02-02 17:08:07 upgrade xserver-xorg 1:7.6+7ubuntu7 1:7.6+7ubuntu7.1
2012-02-02 17:08:09 upgrade xorg 1:7.6+7ubuntu7 1:7.6+7ubuntu7.1[/B]


In a first view, most likely the unity, x11, xserver and xorg updates must have messed it. Now I need to find a way to safely revert it to the previous version and see if it fixes the problem. Bram Gadeyne, can you check if you updated packages match with mine?

---

### Post by paulodeleo on 2012-02-06
I didn't messed up with packages yet, but I finally got a way to show the grub menu. Had to use this settings in my /etc/default/grub :

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_TERMINAL=console
GRUB_GFXMODE=640x480
```

AND shut off the computer, AND pull off the power cord + external vga monitor cable AND hold shift at startup (yep, I tried all simpler combinations many times first).

And then, I choose "Previous Linux versions" grub submenu and decided to try a old 2.6.x kernel option, and TA-DA! Both my displays are working now.

And I think I will never reboot or update my box again :)

Weird, so looks like it really have something to do with the kernel. FWIW, from what I can see in /boot/grub/grub.cfg, the grub menu that is my default and have the bug is:

```
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root 1a887224-285b-46c6-8998-740a8c2c9ddd
        linux   /boot/vmlinuz-3.0.0-15-generic root=UUID=1a887224-285b-46c6-8998-740a8c2c9ddd ro  splash  
        initrd  /boot/initrd.img-3.0.0-15-generic
}
```

And the one that worked fine:

```
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root 1a887224-285b-46c6-8998-740a8c2c9ddd
        linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=1a887224-285b-46c6-8998-740a8c2c9ddd ro  splash  
        initrd  /boot/initrd.img-2.6.38-8-generic
}

```

So, no different parameters between them. It's the kernel. Or a combination of the updated packages AND the 3.0.0-15-generic kernel.

---

