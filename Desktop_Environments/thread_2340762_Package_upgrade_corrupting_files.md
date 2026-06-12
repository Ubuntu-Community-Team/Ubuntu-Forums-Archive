---
title: "Package upgrade corrupting files?"
date: 2016-10-21
forum: Desktop Environments
---

### Post by &amp;KyT$0P# on 2016-10-21
I run Lubuntu 14.04.  My desktop is xfdesktop 4.12.2, and my background is a jpeg image stored in [FONT=Courier New]~/Pictures[/FONT].  I ran the following package operations -
```
Start-Date: 2016-10-21  ********
Commandline: aptdaemon role='role-commit-packages' sender=':1.79'
Install: linux-image-3.13.0-100-generic:amd64 (3.13.0-100.147), linux-image-extra-3.13.0-100-generic:amd64 (3.13.0-100.147), linux-headers-3.13.0-100-generic:amd64 (3.13.0-100.147), linux-headers-3.13.0-100:amd64 (3.13.0-100.147)
Upgrade: apt:amd64 (1.0.1ubuntu2.14, 1.0.1ubuntu2.15), linux-headers-generic:amd64 (3.13.0.98.106, 3.13.0.100.108), update-manager-core:amd64 (0.196.21, 0.196.22), apt-transport-https:amd64 (1.0.1ubuntu2.14, 1.0.1ubuntu2.15), apt-utils:amd64 (1.0.1ubuntu2.14, 1.0.1ubuntu2.15), python3-update-manager:amd64 (0.196.21, 0.196.22), tzdata-java:amd64 (2016f-0ubuntu0.14.04, 2016h-0ubuntu0.14.04), libapt-inst1.5:amd64 (1.0.1ubuntu2.14, 1.0.1ubuntu2.15), libapt-pkg4.12:amd64 (1.0.1ubuntu2.14, 1.0.1ubuntu2.15), tzdata:amd64 (2016f-0ubuntu0.14.04, 2016h-0ubuntu0.14.04), linux-libc-dev:amd64 (3.13.0-98.145, 3.13.0-100.147), update-manager:amd64 (0.196.21, 0.196.22), linux-image-generic:amd64 (3.13.0.98.106, 3.13.0.100.108), linux-generic:amd64 (3.13.0.98.106, 3.13.0.100.108)
End-Date: 2016-10-21  ********

Start-Date: 2016-10-21  ********
Commandline: /usr/sbin/synaptic
Purge: linux-image-extra-3.13.0-92-generic:amd64 (3.13.0-92.139), linux-image-3.13.0-92-generic:amd64 (3.13.0-92.139), linux-headers-3.13.0-92-generic:amd64 (3.13.0-92.139), linux-image-extra-3.13.0-95-generic:amd64 (3.13.0-95.142), linux-image-3.13.0-95-generic:amd64 (3.13.0-95.142), linux-image-extra-3.13.0-93-generic:amd64 (3.13.0-93.140), linux-headers-3.13.0-71:amd64 (3.13.0-71.114), linux-image-3.13.0-93-generic:amd64 (3.13.0-93.140), linux-headers-3.13.0-92:amd64 (3.13.0-92.139), linux-headers-3.13.0-93:amd64 (3.13.0-93.140), linux-headers-3.13.0-95:amd64 (3.13.0-95.142), linux-headers-3.13.0-95-generic:amd64 (3.13.0-95.142), linux-image-extra-3.13.0-71-generic:amd64 (3.13.0-71.114), linux-image-3.13.0-71-generic:amd64 (3.13.0-71.114), linux-headers-3.13.0-93-generic:amd64 (3.13.0-93.140), linux-headers-3.13.0-71-generic:amd64 (3.13.0-71.114)
End-Date: 2016-10-21  ********

```
... and upon rebooting my computer (MacBook Pro) and logging back in, my desktop background was completely grey on the bottom third.

Long story short, I tried to open the desktop background picture in Image Viewer, but it said something about unsupported marker.  So I deleted the image and replaced it with a backup, and it seems OK again.

1) Why did that file suddenly become corrupted?
2) Is there an automatic way to check if other files are likewise corrupted? (Filesystem is ext4.)
3) Are backups the only answer for this type incident?  Or can something else be done to prevent it from happening?


EDIT
Well, I thought fsck was run on all ext4 filesystems during boot, but looks like it skips any filesystems it thinks are clean.  I'm going to manually run fsck on the filesystem then.  Will add the results.

EDIT2 Fired up a 16.04 live system, ran fsck, and got this -
```
$ sudo fsck -n -f /dev/sda5
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 498894/55869440 files (0.3% non-contiguous), 87856968/223473329 blocks

```


EDIT3
This seems not an isolated incident.  Got this when booting -
```
LibClamAV Error: cli_dbgets: Invalid data or internal buffer too small
LibClamAV Error: cli_tgzload: File daily.hdb not correctly loaded
LibClamAV Error: Can't load /var/lib/clamav/daily.cld: Malformed database
ERROR: Malformed database
 * Starting ClamAV daemon clamd       [ fail ]
```

---

### Post by &amp;KyT$0P# on 2016-10-25
Update: I modified [FONT=Courier New]/etc/grub.d/10_linux[/FONT] to boot the 3.13.0-98 kernel instead of the latest version.  And I haven't noticed any further file corruption.

Coincidence?  Or is the .100 kernel the problem?

---

### Post by Bashing-om on 2016-10-25
halogen2; Hey;

> **halogen2 said:**
> Update: I modified [FONT=Courier New]/etc/grub.d/10_linux[/FONT] to boot the 3.13.0-98 kernel instead of the latest version.  And I haven't noticed any further file corruption.

Coincidence?  Or is the .100 kernel the problem?

I too have some reservations about the -100 version as I too have noticed a few anomalies that were not present on the -98 kernel . Thus far I can accept and work-around and after a bios upgrade ( chip replacement) will then see what I need to do .

[INDENT][INDENT]in the end
[INDENT][INDENT][INDENT]it's all good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-10-25
Thanks for your insight Bashing-om.  It sounds like we found the culprit.  I will definitely stick to the .98 kernel for now.

Where can we find useful and informative changelogs for the kernel updates?

---

### Post by Bashing-om on 2016-10-25
halogen2; Welp;

For my use case kernel -100 is doable - with but one work-a-round .. and the probability to re-install some firmwares ! ./..
I have yet to understand why some of the updates on the -98 kernel did not carry over ( pciids, usbids, nvidia-firmware, ect )

Mind ya I have not read the changelog . So ... whatever .

Changelogs:
[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_3.13.0-100.147/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_3.13.0-100.147/changelog)

EDIT: there is also :
```

apt-get changelog <package>

```
Kernel -101 is right around the corner .. see what then happens :)

[INDENT][INDENT]because ubuntu
[INDENT][INDENT][INDENT]we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-10-25
> **Bashing-om said:**
>  nvidia-firmware, 
Interesting you should mention Nvidia.  This machine has the "recommended" Nvidia proprietary drivers installed, for the discrete Nvidia GPU, although I haven't used it recently.

Do you think this could be related to our troubles?

> Changelogs:
Nice, thanks for that link! 8-)
I'll keep an eye on it.

> EDIT: there is also :
```

apt-get changelog <package>

```
Nope, not for kernels, which is why I asked.  When I grab changelogs through aptitude or Update Manager, it just says something like "linux ABI" followed by the version number of the package.

---

### Post by Bashing-om on 2016-10-25
halogen2; Uh HUh /

In respect to nVidia not playing nice.
Apt has this to say:
> 
Description: Firmware for nVidia graphics cards
 Contains the firmware-like context programs for the
 open-source nouveau nVidia drivers.  These are required for
 acceleration (both 2D and 3D) on nVidia cards of the nv40 generation
 and above (GeForce6 and above).
 .
 Although the nouveau drivers are now able to generate this firmware for
 nv40 generation cards this package still contains the nvidia context programs
 for debugging purposes.
 .
 This package is temporary; the nouveau drivers will soon be able to
 generate this data on the fly.

sysop@1404mini:~$ dpkg -l nouveau-firmware
dpkg-query: no packages found matching nouveau-firmware
sysop@1404mini:~$ 

Which makes me pause if we can accept the nouveau driver at face value .

Mind ya
[INDENT][INDENT]it's buntu - where there is a will there is a way[/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-10-25
Ok then it's likely not related.

Incidentally, the [list of changes for the .101 kernel]("http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_3.13.0-101.148/changelog") is pretty big.  Seems worth a shot.

Plan of action -
1) Wait for next kernel upgrade (in the mean time keep using .98)
2) Backup system **before** updating
3) Update and try the newer kernel
4) If no issues, purge .100 and reset default kernel in GRUB

Guess I can mark this thread solved now.  Thank you again Bashing-om for your help.

---

### Post by yetimon_64 on 2016-10-25
> **halogen2 said:**
> ...
Coincidence?  Or is the .100 kernel the problem?

On upgrading to that particular kernel I also got scrambled graphics. Ended up with a mirror image of my top panel and about an inch of "Grey" screen plastered over the bottom of my desktop. I could still right click on it and get the xfdesktop menu etc, but it totally wrecked the display as such including obscuring the bottom inch or so of my conky set up.

I tried switching the display between the laptop screen and my external monitor, the scrambled graphics followed the primary display only with the second display working perfectly fine irrespective of which screen it was output onto.

> **halogen2 said:**
> Interesting you should mention Nvidia.  This machine has the "recommended" Nvidia proprietary drivers installed, for the discrete Nvidia GPU, although I haven't used it recently.

Do you think this could be related to our troubles?...
I use the nvidia proprietary drivers here as well. I have dual intel/nvidia graphics hardware and am using the 340.96 driver. From the inxi command ...

```
Graphics:  Card: Intel Broadwell-U Integrated Graphics X.Org: 1.15.1 drivers: nvidia,intel Resolution: 1920x1080@60.0hz 
           GLX Renderer: GeForce GTX 850M/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 340.96

```

After altering the display properties a few times trying to get the screen to clear I tried resetting the xserver from a tty terminal (sudo service lightdm restart) with no change. Finally a full reboot reset whatever was happpening for me luckily and has held stable since.

---

### Post by &amp;KyT$0P# on 2016-10-25
> **yetimon_64 said:**
> On upgrading to that particular kernel I also got scrambled graphics. Ended up with a mirror image of my top panel and about an inch of "Grey" screen plastered over the bottom of my desktop. I could still right click on it and get the xfdesktop menu etc, but it totally wrecked the display as such including obscuring the bottom inch or so of my conky set up.
Yep, sounds like a similar problem.  But most stuff would draw fine on top of the grey here, such as my bottom lxpanel and the context menu.

For comparison, my inxi output -
```
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0 chip-ID: 8086:0166 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1440x900@59.9hz 
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes

```
And the Nvidia stuff -
```
$ dpkg-query -W | grep -i nvidia
nvidia-352      352.63-0ubuntu0.14.04.1
nvidia-opencl-icd-352   352.63-0ubuntu0.14.04.1
nvidia-prime    0.6.2
nvidia-settings 331.20-0ubuntu8

```


If any of you get the next kernel upgrade before me, please let me know how it works out.  I will also report back with my own results.

---

### Post by yetimon_64 on 2016-10-25
> **halogen2 said:**
> If any of you get the next kernel upgrade before me, please let me know how it works out.... I'll keep an eye on the next upgrade when it comes through and report back, this current -100 kernel works fine now here. Whatever went astray seemed to correct itself after a reboot.

Only real similarity in our outputs I am noting is the version of xorg being 1.15.1, you are using the mesa glx rendering while I am using nvidia. Interesting.

---

### Post by Bashing-om on 2016-10-25
halogen2; Hey !

I take note that:
> **halogen2 said:**
> Yep, sounds like a similar problem.  But most stuff would draw fine on top of the grey here, such as my bottom lxpanel and the context menu.

For comparison, my inxi output -
```
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0 chip-ID: 8086:0166 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1440x900@59.9hz 
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes

```
And the Nvidia stuff -
```
$ dpkg-query -W | grep -i nvidia
nvidia-352      352.63-0ubuntu0.14.04.1
nvidia-opencl-icd-352   352.63-0ubuntu0.14.04.1
nvidia-prime    0.6.2
nvidia-settings 331.20-0ubuntu8

```


If any of you get the next kernel upgrade before me, please let me know how it works out.  I will also report back with my own results.

> 
nvidia-352      352.63-0ubuntu0.14.04.1
nvidia-settings 331.20-0ubuntu8

would it not be best if "nvidia-settings" matched the version of the driver installed ?

[INDENT][INDENT]jeep it clean behind
[/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-10-25
I noticed that as well.  Quick search in Synaptic indicates that's the only version of nvidia-settings available from the repositories.

Nvidia graphics was a right pain to get working.  Generally, I rather let sleeping dogs be. ;)

---

### Post by Bashing-om on 2016-10-26
halogen2l Well ..

when you are right, you are right:
> 
 Quick search in Synaptic indicates that's the only version of nvidia-settings available from the repositories.

[http://packages.ubuntu.com/search?keywords=nvidia-settings](http://packages.ubuntu.com/search?keywords=nvidia-settings)
The 331 version of nvidia-settings is what is the offer .

That I guess Is what I get for grasping at straws. huh .

[INDENT][INDENT]but the ship is not going down
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-11-09
> **halogen2 said:**
> Yep, sounds like a similar problem.  But most stuff would draw fine on top of the grey here, such as my bottom lxpanel and the context menu.

For comparison, my inxi output -
```
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0 chip-ID: 8086:0166 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1440x900@59.9hz 
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes

```
And the Nvidia stuff -
```
$ dpkg-query -W | grep -i nvidia
nvidia-352      352.63-0ubuntu0.14.04.1
nvidia-opencl-icd-352   352.63-0ubuntu0.14.04.1
nvidia-prime    0.6.2
nvidia-settings 331.20-0ubuntu8

```


If any of you get the next kernel upgrade before me, please let me know how it works out.  I will also report back with my own results.


Well; halogen2;

This day I got and installed kernel version -101 . Sadly the drivers for my nVidia card are not backported to this release either . I will have to continue to live with "nomodeset" as a boot method.

[INDENT][INDENT]now if I were real good
[INDENT][INDENT]I could do something else about it
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-11-09
Thanks for getting back to me, Bashing-om.

> **Bashing-om said:**
> Well; halogen2;

This day I got and installed kernel version -101 . Sadly the drivers for my nVidia card are not backported to this release either .
Hmm.  Nvidia drivers here updated to 367 two days ago -
```
$ dpkg-query -W | grep -i nvidia
nvidia-352      367.57-0ubuntu0.14.04.1
nvidia-367      367.57-0ubuntu0.14.04.1
nvidia-opencl-icd-367   367.57-0ubuntu0.14.04.1
nvidia-prime    0.6.2
nvidia-settings 331.20-0ubuntu8

```

Do you think that could be promising, or irrelevant for this?

---

### Post by Bashing-om on 2016-11-09
halogen2; Welp;

In my situation that does not help in yours in the least . 

There are things I could do .. The problem I have is that I want to keep my 3.13 series kernel . But with this kernel there is " kepler, unknown chipset" from the kernel  - and from what i can find out, if I wanted to re-compile the kernel, there is a patch available . Later kernels do support this card  ( GT 710 ). If I were to enable the ability to install the proprietary driver with the current kernel, you can not imagine what all the system wants to install on this my beloved minimal install . I choose not even to go there . In my use case for this minimal install 'nomodeset' suffices for all my uses . Good nuf . I gonna leave well enough alone .

On a different front - I have a Samsung SSD that appears that my bios does not accept .  That is now the brunt of efforts to find out the why . Getting 16.04 as a minimal core install working. Even after updating Bios .. The firmware does not integrate the SSD into the system . I got a plan - and the time to consider other means - .. When I make the time to put it in action and see what works out -> then I see what I am going to do . 

Now perhaps it will be time to retire this ole box ??

[INDENT][INDENT][INDENT]worse things could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-11-09
Oh, I see.  Well, off to give this a go...

---

### Post by yetimon_64 on 2016-11-09
> **yetimon_64 said:**
> I'll keep an eye on the next upgrade when it comes through and report back...

Just booted into the 101 kernel with no problems, seems my issues were minor and only a once off occurrence, albeit similar to what you reported originally. Still on the 340.98 nvidia driver here though, no upgrades have been done there.

---

### Post by &amp;KyT$0P# on 2016-11-09
Thanks yetimon_64, that sounds promising.

> **halogen2 said:**
>  I will also report back with my own results.
And so far so good with .101 kernel.  The next few days will tell.

---

### Post by &amp;KyT$0P# on 2016-11-13
Still have no issues with .101 kernel.  Been using it for long enough that if this problem were there, I would have noticed by now.

Case closed for me.

Thanks again Bashing-om and yetimon_64 for all the help. :KS

---

