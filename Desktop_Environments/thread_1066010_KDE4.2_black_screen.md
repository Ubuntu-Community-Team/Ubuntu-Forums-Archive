---
title: "KDE4.2 black screen"
date: 2009-02-10
forum: Desktop Environments
---

### Post by qaws on 2009-02-10
Hello,

I have just tried to install KDE for Ubuntu 9.04, from official Ubuntu repositories as package kde + dependencies.

After install: I can choose KDE in gdm, I can log-in with KDE, but when splash finishes, my screen turns black. I can turn it black immediately without waiting for splash to finish, when I leftclick or rightclick during the splash.
I can see only screen and white cursor, which reacts as my mouse moves. KDE is not controllable - I can switch only states of keyboard LEDs (NumLock, CapsLock), Alt+Tab and Ctrl+Alt+Fx. When I press Alt+Tab, screen gets white (again with mouse cursor) and when I pres Alt+Tab once more, it shows a message "No Windows" in the centre of the screen.

I have tried to do following things (as Google said), but I was unsuccessful, behauvior have not changed.
1.) Turning off composing effects in kwinrc.
2.) Removal of package kwin.
3.) Removal of ~/.kde.
4.) Using newly-created user to log-in.
5.) Reinstall KDE (remove with --purge and then install)
6.) Reboot.
7.) New kernel.
8.) In xorg.conf line 'Driver "nvidia"' -> 'Driver "vesa"'
9.) Reinstall VGA drivers & install new as DKMS module.

Some information about my PC:
Linux masina 2.6.28-7-generic #19-Ubuntu SMP Fri Feb 6 08:29:41 UTC 2009 i686 GNU/Linux
Driver for VGA "NVIDIA-Linux-x86-173.14.15-pkg0.run" (downloaded from Nvidia page) -> last beta, other drivers does neither work with this kernel, nor 3D acceleration is working (tested under Gnome)
System up-to-date

lspci:
[I]00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0b.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600XT] (rev a1)[/I]

Xorg logs are very similar, I did not found any critical difference.
I tried to read dmesg when black screen appears, but there are no fatal errors. After few minutes (and black screen, when it seems PC is doing nothing) I get segfault:
*nepomukservices[9564]: segfault at 720065 ip b5ee98bd sp b3c35fb0 error 4 in librdf.so.0.0.0[b5ed9000+40000]*

If you knew, how to solve this problem (you don't have to be sure), please write it there. I can send any logs you want, if you request them. 
Thanks for reply.

---

### Post by jbrown96 on 2009-02-10
I had a problem sort of like this the other day, but I have ATI graphics hardware. Get into recovery mode with the newest kernel. When the system first boots and the grub appears, you may have to press Escape. Once it boots, choose the root shell option. 

instead of manually configuring the xorg.conf. Try ```
dpkg-reconfigure xserver-Xorg
```. If you have a standard US keyboard. You can just accept all the default configuration options. Once this is done, become your regular user with ```
su - USER
``` but change USER to your username. I'm not completely sure what will happen next since you have multiple desktop environments installed. Try ```
startx
``` If that takes you to Gnome, then try rebooting and logging in as normal. 

If KDE starts and works, then you just need to get the Nvidia driver working. you should try a different version of the driver. According to Nvidia, you should use the pkg2.run file instead of pkg0.run. This is built for more common kernels. It seems like you knew how to install the driver the first time, so I won't go through the procedure again. 

If the system is still not working, I'm not really sure what to do.
You might need to disable Compiz in Gnome. Maybe there are two window managers trying to run.

---

### Post by qaws on 2009-02-10
> **jbrown96 said:**
> I had a problem sort of like this the other day, but I have ATI graphics hardware. Get into recovery mode with the newest kernel. When the system first boots and the grub appears, you may have to press Escape. Once it boots, choose the root shell option. 

instead of manually configuring the xorg.conf. Try ```
dpkg-reconfigure xserver-Xorg
```. If you have a standard US keyboard. You can just accept all the default configuration options. Once this is done, become your regular user with ```
su - USER
``` but change USER to your username. I'm not completely sure what will happen next since you have multiple desktop environments installed. Try ```
startx
``` If that takes you to Gnome, then try rebooting and logging in as normal.
I haven't try it till now, but login via gdm is almost impossible without drivers (it wants to run on low resolution and it does not restart properly). I ran nvidia-xconfig then and it fixed resolution. I will try all your commands and ideas tommorow.

> **jbrown96 said:**
> If KDE starts and works, then you just need to get the Nvidia driver working. you should try a different version of the driver. According to Nvidia, you should use the pkg2.run file instead of pkg0.run. This is built for more common kernels. It seems like you knew how to install the driver the first time, so I won't go through the procedure again.
I have just installed pkg1.run (I have not found anything like pkg2.run) and it seems to have more libraries, but it did not help.

> **jbrown96 said:**
> If the system is still not working, I'm not really sure what to do.
You might need to disable Compiz in Gnome.I hate Compiz and I have it disabled all the time. I've just tried enabling it and it causes similar error as in KDE (I could only stop it and then login again).

> **jbrown96 said:**
> Maybe there are two window managers trying to run.Good idea, I will try to check it tommorow.

Thanks for your reply, I hope it will help me.

---

### Post by jbrown96 on 2009-02-11
I was just looking at Nvidia's driver page. I guess maybe 64-bit is the only version (at least for your card) that has a pkg2.run version. I've been using 64-bit for so long that I didn't even realize this. 


I've figured out what your problem is. 9.04 uses the a new X-server. Unfortunately there are no Nvidia drivers that work with this new version at this time.

---

### Post by qaws on 2009-02-11
> **jbrown96 said:**
> I was just looking at Nvidia's driver page. I guess maybe 64-bit is the only version (at least for your card) that has a pkg2.run version. I've been using 64-bit for so long that I didn't even realize this. 


I've figured out what your problem is. 9.04 uses the a new X-server. Unfortunately there are no Nvidia drivers that work with this new version at this time.Yes, it is possible it uses a new X-server, but how it is possible I have usable Gnome (without composing effects, but with 3D acceleration)?

I don't have a 64-bit system, so I cannot try pkg2.run.

Nevermind, I will try it till it will work. Thank you for your time.

---

