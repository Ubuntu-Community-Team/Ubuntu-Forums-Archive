---
title: "Launcher bar disappeared"
date: 2012-07-11
forum: Desktop Environments
---

### Post by jlapinski4 on 2012-07-11
Anyone have this issue: suddenly all the text in any open window was shadowed in black boxes (letters were white, surrounded by black). I rebooted and that issue was gone by the launcher bar disappeared?

---

### Post by jmfal on 2012-07-11
Run this in a terminal:

```
 unity --reset    
```

---

### Post by jlapinski4 on 2012-07-11
> **jmfal said:**
> Run this in a terminal:

```
 unity --reset    
```


Thanks!  I just tried that and this is what I get:

(compiz:3315): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Initializing staticswitcher options...done
WARN  2012-07-11 22:16:39 unity.libindicator <unknown>:0 Desktop file '/usr/share/app-install/desktop/thunderbird:thunderbird.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-11 22:16:39 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-11 22:16:39 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-11 22:16:39 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-11 22:16:39 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
ERROR 2012-07-11 22:16:39 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"

And the launcher doesn't return.

---

### Post by jlapinski4 on 2012-07-11
I know this is a lot of code, but this is what I get:

:~$ unity--reset
unity--reset: command not found
jeffrey@Ubook:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
DRM_IOCTL_I915_GEM_CONTEXT_CREATE failed: Invalid argument
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:2209): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Initializing staticswitcher options...done
ERROR 2012-07-11 22:20:30 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2012-07-11 22:20:30 unity.libindicator <unknown>:0 Desktop file '/usr/share/app-install/desktop/thunderbird:thunderbird.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-11 22:20:30 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-11 22:20:30 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-11 22:20:30 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-11 22:20:30 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.

Any advice is much appreciated by this Ubuntu neophyte!

---

### Post by Dr. Tyrell on 2012-07-11
I haven't had rendering problems, but did notice the GEM_CONTEXT_CREATE error in glxinfo:


drtyrell@drtyrell-700Z7C ~ $ glxinfo
name of display: :0
DRM_IOCTL_I915_GEM_CONTEXT_CREATE failed: Invalid argument
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
...

The Doctor

---

### Post by jlapinski4 on 2012-07-12
Booting in 2d brings the launcher back, however the problem hasn't been fixed. Still eliciting ideas and advice.

I will likely reinstall Ubuntu when I am back in my home office if I am unable to resolve the issue.

---

### Post by sudo smith on 2012-07-12
Get this problem when I open Libre Office. A couple other users have also experienced this problem (normally when booting). Seems to be a nvidia driver problem (advice that I got is to either just run in Ubunutu 2d or downgrade your nvidia driver). Hope this helps.

---

### Post by jlapinski4 on 2012-07-12
> **sudo smith said:**
> Get this problem when I open Libre Office. A couple other users have also experienced this problem (normally when booting). Seems to be a nvidia driver problem (advice that I got is to either just run in Ubunutu 2d or downgrade your nvidia driver). Hope this helps.

Thanks! 2d seems to be working although I cannot run updates.  I am considering just re-loading as I am wondering if my inexperience with Linux is the problem!  I have been trying to install a specific software package and that was when I began to have all the problems.

---

### Post by jmfal on 2012-07-12
Try this in terminal and post the results between the ```
[code] brackets using #

[CODE]  /usr/lib/nux/unity_support_test -p      
```

I quit playing with compiz and use 2D, too many problems just like you are having.

---

### Post by jlapinski4 on 2012-07-12
> **jmfal said:**
> Try this in terminal and post the results between the ```
[code] brackets using #

[CODE]  /usr/lib/nux/unity_support_test -p      
```I quit playing with compiz and use 2D, too many problems just like you are having.


I will run this and post the results. I can't seem to run updates in 2d. I get this:

Your system does not contain a ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or edubuntu-desktop package and it was not possible to detect which version of Ubuntu you are running.
 Please install one of the packages above first using synaptic or apt-get before proceeding.

---

### Post by jlapinski4 on 2012-07-12
DRM_IOCTL_I915_GEM_CONTEXT_CREATE failed: Invalid argument
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string:  3.0 Mesa 8.1-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

---

### Post by jlapinski4 on 2012-07-12
> **jmfal said:**
> Try this in terminal and post the results between the ```
[code] brackets using #

[CODE]  /usr/lib/nux/unity_support_test -p      
```I quit playing with compiz and use 2D, too many problems just like you are having.
[CODE
DRM_IOCTL_I915_GEM_CONTEXT_CREATE failed: Invalid argument
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string:  3.0 Mesa 8.1-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
[/CODE]

---

### Post by jmfal on 2012-07-12
Try  to install the desktop and see if that helps

---

### Post by jlapinski4 on 2012-07-12
> **jmfal said:**
> Try  to install the desktop and see if that helps

Here is what I get when I try to install the desktop. Something has me locked out.

jeffrey@Ubook:~$ sudo apt-get install ubuntu-desktop
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by jmfal on 2012-07-12
Do you have the software center or update manager open?

run this to unlock and try again

```
   sudo rm /var/lib/dpkg/lock   
```

---

### Post by jlapinski4 on 2012-07-12
> **jmfal said:**
> Do you have the software center or update manager open?

run this to unlock and try again

```
   sudo rm /var/lib/dpkg/lock   
```

```
 jeffrey@Ubook:~$ sudo rm /var/lib/dpkg/lock
[sudo] password for jeffrey: 
jeffrey@Ubook:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up moneydance (2011.803) ...
Preparing JRE ...
/var/lib/dpkg/info/moneydance.postinst: 22: /var/lib/dpkg/info/moneydance.postinst: bin/unpack200: not found
Error unpacking jar files. Aborting.
dpkg: error processing moneydance (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.
 
```

Ok that worked to unlock, but above is the errors I have been getting, and what seems to have led to the problems I ran into with the launcher in 3D.  

I had tried to configure Thunderbird and since have been getting the error about qmail, and tried to install the program Moneydance which also has caused me grief. I need to install java-7 in order to run Moneydance and while I was trying to install it I ran into all the issues with the launcher.

---

### Post by jmfal on 2012-07-12
I've tried to find something about the fqdn , you'll have to do some research on that,set it up and reinstall moneydance 

Try this to remove moneydance 

```
  sudo apt-get purge moneydance
```

If that doesn't remove it try adding the rest (.postinst) and then you can update.

---

### Post by jlapinski4 on 2012-07-12
> **jmfal said:**
> I've tried to find something about the fqdn , you'll have to do some research on that,set it up and reinstall moneydance 

Try this to remove moneydance 

```
  sudo apt-get purge moneydance
```If that doesn't remove it try adding the rest (.postinst) and then you can update.

Thank you!  That removed all but one file 

```
rm: cannot remove `/usr/share/applications/moneydance.desktop': No such file or directory
   
```

---

### Post by jmfal on 2012-07-12
Try
```
 sudo apt-get purge moneydance.desktop   
```

---

### Post by jlapinski4 on 2012-07-12
> **jmfal said:**
> Try
```
 sudo apt-get purge moneydance.desktop   
```


```
 jeffrey@Ubook:~$ sudo apt-get purge moneydance.desktop
[sudo] password for jeffrey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package moneydance.desktop
E: Couldn't find any package by regex 'moneydance.desktop' 
```

I am certain that I messed something up! When I update via terminal it appears to get the updates, however the update manager states that there are available updates but will not allow me to run them. 

When I log in to 3d all that I get is the background picture for the desktop and it is non functional.

I am going to reboot and see if that helps anything.

Thank you for all of your help, I very much appreciate it!

---

### Post by jmfal on 2012-07-12
I think that last file is the problem with the fqdn, its not completely installed

TRY
```
 sudo apt-get clean  
               sudo apt-get autoremove
               sudo apt-get autoclean  
```
               
And try to update/upgrade.

---

### Post by jlapinski4 on 2012-07-12
Your system does not contain a ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or edubuntu-desktop package and it was not possible to detect which version of Ubuntu you are running.
 Please install one of the packages above first using synaptic or apt-get before proceeding.

  Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'ubuntu-desktop' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

---

### Post by jmfal on 2012-07-12
I don't know what to tell you.

With all the aggravation trying to get a desktop and everything else, you could reinstall Ubuntu and eliminate all the hassle.

Try rebooting to the grub screen >> go into the recovery kernal >> low graphics mode>>open a terminal and install the ubuntu desktop

```
  sudo apt-get install ubuntu-desktop
```

I think you will have to restart after that  and login to the 2D

---

### Post by jlapinski4 on 2012-07-12
> **jmfal said:**
> I don't know what to tell you.

With all the aggravation trying to get a desktop and everything else, you could reinstall Ubuntu and eliminate all the hassle.

Try rebooting to the grub screen >> go into the recovery kernal >> low graphics mode>>open a terminal and install the ubuntu desktop

```
  sudo apt-get install ubuntu-desktop
```I think you will have to restart after that  and login to the 2D

No worries, I am leaning toward a reinstallation. This is my first time using any Linux OS and bought this laptop specifically for that purpose.  I haven't migrated all of my files, media, etc from my Mac yet - as I want to get comfortable with Ubuntu first. 

All of you help and time has been greatly appreciated!

---

### Post by jmfal on 2012-07-12
I think starting fresh will be better

You know what you need to do to get those apps running right, and hopefully you know what not to do.

Good luck

---

### Post by jlapinski4 on 2012-07-12
> **jmfal said:**
> I think starting fresh will be better

You know what you need to do to get those apps running right, and hopefully you know what not to do.

Good luck

Thanks!  I think I am steering clear of "moneydance" though,  I will use a financial program already known and compatible with Ubuntu at least until I am a bit more Linux savvy.  

Thanks again for your support and assistance!

---

### Post by jlapinski4 on 2012-07-14
As an interesting FYI - I reinstalled Ubuntu and while installing the ppa to get my trackpad to work properly I am running into the EXACT same problem as I did previously. The launcher bar disappears!!

---

### Post by jmfal on 2012-07-14
Are you usung Unity 3D or 2D.

I f you hold pointer over edge of screen does launcher popup.

What kind of graphics card do you have and did you install proprietary drivers?

---

### Post by jlapinski4 on 2012-07-14
> **jmfal said:**
> Are you usung Unity 3D or 2D.

I f you hold pointer over edge of screen does launcher popup.

What kind of graphics card do you have and did you install proprietary drivers?


I am giving 3D one last chance.  No, the launcher doesn't reappear when I hover. I did check the settings to be sure it was in "invisible" mode. Seemed to all take place after downloading a ppa for the trackpad. 

I believe its nvidia - but now I am wondering if this may be the problem. When I open system settings it has the graphics card info as "unknown"

---

### Post by jlapinski4 on 2012-07-15
> **jlapinski4 said:**
> I am giving 3D one last chance.  No, the launcher doesn't reappear when I hover. I did check the settings to be sure it was in "invisible" mode. Seemed to all take place after downloading a ppa for the trackpad. 

I believe its nvidia - but now I am wondering if this may be the problem. When I open system settings it has the graphics card info as "unknown"


Yes, I did install the proprietary drivers.

---

### Post by jmfal on 2012-07-15
Can you open a terminal if you login to 2D ?

You should remove ppa for trackpad using "ppa-purge"

```
 sudo apt-get install ppa-purge     
```

And reinstall later

Run
```
  lspci -v  
```

and copy/paste output between ```
[CODE] brackets using #  and
[CODE] lspci -nnk | grep -A2 VGA    
```

---

### Post by jlapinski4 on 2012-07-15
Yes, 2D is unaffected and unlike the last time this happened I am able to update and install other software without issues.

I will try your suggestions tomorrow. 

What will the 2nd lines of code that you suggested do?

---

### Post by jmfal on 2012-07-16
The "lpci -v " will list all hardware on pc, and kernals (drivers in use).

The last one give info about video card and I wanted to see if they match up.

I think you have a problem with your graphics driver, because of trouble running 3D

---

### Post by jlapinski4 on 2012-07-16
> **jmfal said:**
> Can you open a terminal if you login to 2D ?

You should remove ppa for trackpad using "ppa-purge"

```
 sudo apt-get install ppa-purge     
```And reinstall later

Run
```
  lspci -v  
```and copy/paste output between ```
[CODE] brackets using #  and
[CODE] lspci -nnk | grep -A2 VGA    
```

```
 jeffrey@Ubook31A:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:04.0 Signal processing controller: Intel Corporation Device 0153 (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at dfe08000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, medium devsel, latency 0, IRQ 43
    Memory at f7d00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f7d22000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7d20000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f7d18000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: f7c00000-f7cfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7d1f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f060 [size=32]
    Memory at f7d1e000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: medium devsel, IRQ 10
    Memory at f7d1d000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation Panther Point Thermal Management Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 1517
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f7d1c000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7c00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
     
```

---

### Post by jlapinski4 on 2012-07-16
> **jmfal said:**
> The "lpci -v " will list all hardware on pc, and kernals (drivers in use).

The last one give info about video card and I wanted to see if they match up.

I think you have a problem with your graphics driver, because of trouble running 3D


```
 jeffrey@Ubook31A:~$ lspci -nnk | grep -A2 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1517]
    Kernel driver in use: i915
   
```

---

### Post by jmfal on 2012-07-16
What is the output of the last command

That is on-board video right

---

### Post by jmfal on 2012-07-16
If everything is running smooth I would just use the driver you have and stay away from 3D.
I found one ppa that has drivers for intel but you might have problems running 3D anyway.

[https://launchpad.net/~glasen/+archive/intel-driver]("https://launchpad.net/%7Eglasen/+archive/intel-driver")

Any problems, post back

---

### Post by jlapinski4 on 2012-07-16
> **jmfal said:**
> If everything is running smooth I would just use the driver you have and stay away from 3D.
I found one ppa that has drivers for intel but you might have problems running 3D anyway.

[https://launchpad.net/~glasen/+archive/intel-driver]("https://launchpad.net/%7Eglasen/+archive/intel-driver")

Any problems, post back

```
 jeffrey@Ubook31A:~$ lspci -nnk | grep -A2 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1517]
    Kernel driver in use: i915
 
```

Everything is running very well in 2D and I plan on sticking with that. Oddly when I ran the ppa - purge command my trackpad is still functional (perhaps they weren't all removed).

---

### Post by jmfal on 2012-07-16
You wanted to get trackpad working right?

Are by chance using a laptop?

---

### Post by jlapinski4 on 2012-07-16
> **jmfal said:**
> You wanted to get trackpad working right?

Are by chance using a laptop?


Yes, I am using a ASUS X31A zenbook.  The track pad is actually working well. I checked the 3D mode once and still no launcher but in 2D everything works. 

What is the difference between 2 and 3 D?

---

### Post by jmfal on 2012-07-16
Maybe this will explain better than I can

[http://askubuntu.com/questions/34913/what-is-the-difference-between-unity-2d-and-unity-3d](http://askubuntu.com/questions/34913/what-is-the-difference-between-unity-2d-and-unity-3d)

And 
[http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d](http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d)

There may be more differences........

---

### Post by jlapinski4 on 2012-07-17
> **jmfal said:**
> Maybe this will explain better than I can

[http://askubuntu.com/questions/34913/what-is-the-difference-between-unity-2d-and-unity-3d](http://askubuntu.com/questions/34913/what-is-the-difference-between-unity-2d-and-unity-3d)

And 
[http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d](http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d)

There may be more differences........

thank you!

---

