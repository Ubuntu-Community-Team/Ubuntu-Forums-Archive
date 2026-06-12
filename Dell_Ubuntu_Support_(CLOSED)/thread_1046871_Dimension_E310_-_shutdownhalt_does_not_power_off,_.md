---
title: "Dimension E310 - shutdown/halt does not power off, restart ok"
date: 2009-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tereg on 2009-01-21
I'm a first time poster, and relatively new with using GNU/Linux on a regular basis, but I will try to be as specific and verbose about my problem as reasonably possible and detail out what I have tried to do to troubleshoot this issue.

I'm using Intrepid...

```

$ uname -a
Linux teregmaindell 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

$ cat /proc/version_signature 
Ubuntu 2.6.27-9.19-generic

```If I attempt to shut down/power off the computer upon reaching either the gdm login screen, or after logging in, the computer will not completely power off after the Will now halt message is displayed in terminal output.  The CPU fan accelerates to top speed, the power light remains on and hardware devices still have power (so I can still do things like eject the CD drive).

If I boot into recovery mode, drop into root and issue the command

```

# shutdown -h now

```or

```

# shutdown -hP now

```it powers off with no problem

I have attached a .zip file to this post with the following contents :

```

$ dmesg > dmesg.out
$ sudo dmidecode > dmidecode.out
$ lshal > lshal.out
$ sudo lshw > lshw.out
$ sudo lspci -vvnn > lspci-vvnn.out
$ sudo cat /boot/grub/menu.lst > menu.lst.out
$ cat /etc/X11/xorg.conf > xorg.conf.out

```What I have attempted thus far (I will link the source when necessary)

[LIST]
[*]Editing grub menu to incorporate
[/LIST]
```
acpi=force lapic
``` and just ```
acpi=force
```I should note that each time I edited grub I issued

```
$ sudo update-grub
```before rebooting

[http://ubuntuforums.org/showthread.php?t=187186](http://ubuntuforums.org/showthread.php?t=187186)
[http://ubuntuforums.org/showthread.php?t=809311](http://ubuntuforums.org/showthread.php?t=809311)

My desktop visualization/Appearance settings were already set to None when I attempted this.

This resulted in no change in behavior

[LIST]
[*]Edited /etc/modules to incorporate
[/LIST]
```
apm power_off=1
```This resulted in no change in behavior

[LIST]
[*]Used both ```
apm power_off=1
``` in /etc/modules and ```
acpi=off apm=power_off
``` in the grub menu list
[/LIST]
After rebooting with this option in grub, the system halted before the login screen

[http://ubuntuforums.org/showthread.php?t=998981](http://ubuntuforums.org/showthread.php?t=998981)
[http://ubuntuforums.org/archive/index.php/t-417028.html](http://ubuntuforums.org/archive/index.php/t-417028.html)

I found out that the option acpi=off caused the halt.  After removing this option I was able to boot all the way to the login prompt.


[LIST]
[*]The alsa-utils bug that was somewhat related to this issue did not apply to me as terminal output did not seem to hang or stop when shutting down alsa
[/LIST]
I checked a few other places

```

$ cat /etc/default/halt 
# Default behaviour of shutdown -h / halt. Set to &quot;halt&quot; or &quot;poweroff&quot;.
HALT=poweroff

```This was like this the whole time.

```

$ sudo apt-get install acpi-support
Reading package lists... Done
Building dependency tree       
Reading state information... Done
acpi-support is already the newest version.

```I noticed something curious in syslog

```

$ cat /var/log/syslog | grep ACPI

<snip>
[    0.018597] ACPI: Core revision 20080609
[    0.034640] ACPI: Checking initramfs for custom DSDT
[    0.540764] ACPI: bus type pci registered
[    0.544693] ACPI: EC: Look up EC in DSDT
[    0.567786] ACPI: BIOS _OSI(Linux) query ignored
[    0.567861] ACPI: DMI System Vendor: Dell Inc.                
[    0.567935] ACPI: DMI Product Name: Dell DV051                   
[    0.568009] ACPI: DMI Product Version: 
[    0.568034] ACPI: DMI Board Name: 0JC474
[    0.568106] ACPI: DMI BIOS Vendor: Dell Inc.                
[    0.568179] ACPI: DMI BIOS Date: 04/04/2006
[    0.568250] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
[    0.568325] ACPI: If &quot;acpi_osi=Linux&quot; works better, please notify linux-acpi@vger.kernel.org
<snip>

```so I tried the acpt_osi=Linux option in grub, but that did not change any behavior.

I checked Dell's support site with respect to my BIOS version, it is the latest version they have listed for my model.

I didn't really find anything useful from linux.dell.com that I didn't already find in other threads.

I do have a Radeon x1550 video card.  I noticed a few threads where fglrx might have been causing some problems.  I had been using the proprietary fglrx driver, and tried variations of disabling that and using both default xorg configurations and enabling the driver but incorporating ATI big desktop (I am using two monitors off of the video card), but any permutation of that didn't change the halt/shut down behavior.  I am currently using the defaulted xorg configuration from ```
dpkg-reconfigure xserver-xorg
```and then added a virtual display via System -> Preferences -> Screen Resolution  as shown in the .zip file I've attached.

I'm not really sure what direction to go from here.  If any of you can point me in the right direction, I'd appreciate it.  Thanks.

---

### Post by tereg on 2009-01-22
I should also note that if I put the computer into Suspend mode, then it will successfully go into a sleep state.  But if I wake the computer out of sleep state, I have no ability to use any input peripheral, neither keyboard nor mouse (I have to use USB keyboard and mouse for this particular model) and I'm forced to hard power it off.

---

### Post by tereg on 2009-01-28
After doing more research and tweaking, which included compiling a custom kernel, using workarounds on the S90halt script in /etc/rc0.d/, and doing a completely fresh install of Ubuntu, I finally came upon something that worked for me.

Referencing this bug:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255838](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255838)
which referenced this:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/43961](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/43961)

I modified /etc/default/halt and added a line to remove the snd_hda_intel module

This is what it looks like now:

```
# Default behaviour of shutdown -h / halt. Set to "halt" or "poweroff".
/sbin/rmmod snd_hda_intel
HALT=poweroff
```After modifying this, it now shuts down properly.

---

