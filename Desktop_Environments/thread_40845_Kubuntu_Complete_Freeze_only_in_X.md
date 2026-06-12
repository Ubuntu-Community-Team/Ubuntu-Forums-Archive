---
title: "Kubuntu Complete Freeze only in X"
date: 2005-06-10
forum: Desktop Environments
---

### Post by barnone on 2005-06-10
I recently installed Kubuntu the other day and I experience frequent system hangs when in KDE.  These are complete system hangs where I can't get to any terminals (ctrl alt f1-f6) nor does ctrl + alt+ del work for rebooting or ctrl + alt + backspace to kill X.  I have noticed that almost everytime before I get full hang, I get these messages continually scrolling in /var/log/messages:

/var/log/messages error log:   

<CUT>

Jun  9 20:19:29 localhost kernel:  [process_timeout+0/9] process_timeout+0x0/0x9
Jun  9 20:19:29 localhost kernel:  [do_poll+162/193] do_poll+0xa2/0xc1
Jun  9 20:19:29 localhost kernel:  [sys_poll+335/527] sys_poll+0x14f/0x20f
Jun  9 20:19:29 localhost kernel:  [sys_gettimeofday+59/127] sys_gettimeofday+0x3b/0x7f
Jun  9 20:19:29 localhost kernel:  [__pollwait+0/199] __pollwait+0x0/0xc7
Jun  9 20:19:29 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75
Jun  9 20:19:30 localhost kernel:  [schedule+2833/2838] schedule+0xb11/0xb16
Jun  9 20:19:30 localhost kernel:  [__mod_timer+235/292] __mod_timer+0xeb/0x124
Jun  9 20:19:30 localhost kernel:  [schedule_timeout+115/199] schedule_timeout+0x73/0xc7
Jun  9 20:19:30 localhost kernel:  [process_timeout+0/9] process_timeout+0x0/0x9
Jun  9 20:19:30 localhost kernel:  [do_poll+162/193] do_poll+0xa2/0xc1
Jun  9 20:19:30 localhost kernel:  [sys_poll+335/527] sys_poll+0x14f/0x20f
Jun  9 20:19:30 localhost kernel:  [sys_gettimeofday+59/127] sys_gettimeofday+0x

</CUT>

These messages scroll continuously until I experience a full system hang/freeze.

I tried switching from the fglrx to the ati driver for my video card, but it still happenes.  I have had it happen on 2.6.10-5-386, 2.6.10-6-686-smp, and 2.6.11-1-686-smp.  It seems to happen about 3-5 minutes after logging into KDE.  I have had it happen when in firefox, konsole upgrading packages through apt, and even once when clicking the K menu button.  So I don't think a certain app is causing the crash.

I have used many distros with this box, so I know the box is fine.  I previously had SuSE 9.3 on here and never experieced these issues.

Has anyone come across this or know any solutions?  By the way I did a test last night and I left KDM up but didn't login and did a bunch of stuff from the command line and had no problems.  I even ran "crashme" (crash program in apt) for 3 hours with no issues.

Sys Specs:

P4 3.06GHz w/ Hyperthreading
1GB RAM
Asus P4PE Motherboard
ATI Radeon 9800 Pro 128MB

Any suggestions?

---

### Post by barnone on 2005-06-10
After doing a lot of research in these forums, it seems like I am not the only one experiencing this issue.

I tried some of the suggested fixes, but I am still having issues.  Also according to me "disabling 3D acceleration, acellrender etc" is out of the question.  That is not a viable solution.  I would have bought a $15 PCI video card if I wanted subpar video performance.  I would rather go back to SuSE 9.3 where I didn't have these problems.

<bump>

Any one?  Has anyone found out how to fix this?  I think I am the first the actually post kernel message log information from before the crashes.

-barnone

---

### Post by barnone on 2005-06-10
Ok, after some more investigation it seems that I can reproduce this error 100% of the time instantly when executing heavy I/O.

For instance if I do an apt-get dist-upgrade or apt-get install openoffice.org2, it will download the packages fine, but when it is doing the package extraction/installation, I can always have it freeze on me with those errors I detailed before and it will scroll until I get a hard lock causing me to hit the reset button.  Also right before it hangs completely I get 100% CPU utilization according to gkrellm.

For kicks to see if it would help, I booted with acpi off and noapic.  I also shutdown apmd, powernod, and acpi at boot before trying this to see if that made a difference and I still having freezing issues.  :( 

Just some more information in case anyone is actually reading this thread or has a similiar problem :)

---

### Post by barnone on 2005-06-10
Ok, after some more investigation it seems that I can reproduce this error 100% of the time instantly when executing heavy I/O.

For instance if I do an apt-get dist-upgrade or apt-get install openoffice.org2, it will download the packages fine, but when it is doing the package extraction/installation, I can always have it freeze on me with those errors I detailed before and it will scroll until I get a hard lock causing me to hit the reset button.  Also right before it hangs completely I get 100% CPU utilization according to gkrellm.

For kicks to see if it would help, I booted with acpi off and noapic.  I also shutdown apmd, powernod, and acpi at boot before trying this to see if that made a difference and I still having freezing issues.  :( 

Just some more information in case anyone is actually reading this thread or has a similiar problem :)

---

### Post by Chireru on 2005-06-15
I am having the same problem as you, using completely different hardware.

I have opened a bug for it:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11479](https://bugzilla.ubuntu.com/show_bug.cgi?id=11479)

---

### Post by number nine on 2005-08-07
I'm not sure if this is related, but I'm getting a freeze only in X in Kubuntu as well. This usually happens before the KDE splash screen disappears, usually within 5-60 seconds of X starting. This is a hard hang, and I can't do anything with the system.

If I switch to the text console when X starts to load, I can use the text console as much as I want. If I switch to X from the text console, it will result in an immediate system hang.

Unlike the original poster, if I switch to a non-smp kernel, the system works fine (that's how I'm using it now). I've tried going back to earlier smp kernels, but all of them seem to have this issue, so it may not be kernel-specific. I haven't tried disabling hyperthreading in the BIOS and using an SMP kernel, but I'll try that now.

I was using this same system on a (slightly) older version of Kubuntu, with an SMP kernel, with no issues. I re-installed recently, and I've been getting this hang, unless I use a non-smp kernel. 

So the major issues seem to be (at least in my case):
- related to X (console is fine, even with X running in the background)
- related to SMP and/or hyperthreading
- seems to be related to a Kubuntu/X component, not the kernel

I have a *very* similar system to the original poster:

P4 3.0GHz w/ Hyperthreading
512MB RAM
Asus P4C800 Motherboard
ATI Radeon 9800 Pro 128MB, also happens with ATI Radeon 7000

---

### Post by number nine on 2005-08-09
As expected, I can run with an SMP kernel if I disable hyperthreading in the BIOS. Must be a race conditon somewhere in the kubuntu-specific code. I have a feeling this one isn't going to be root-caused and fixed any time soon.  :???:

---

### Post by jamesrw on 2005-08-17
KDE is freezing for me as well as it reads "restoring session". I've never had a session on this new notebook to begin with. Any leads yet?

---

### Post by oskar.norin on 2005-08-18
Same problem for me, tried to upgrade to smp kernel 2.6.11-1-686-smp, 2.6.10-5-686-smp but both craches when I try to startx, as sad earlier in the thread, if I stick to console it does not crash.
Downgraded to 386 kernel without smp and it works fine now, but I miss hyper-threading!
Hope there is a solution out soon because hypertheading works in debian so I will change back but I'am lacy and would like to stick to Ubuntu.

---

### Post by jamesrw on 2005-08-18
i fixed the problem by commenting out this line in Section "Module":
#     Load   "dri"

and added the following lines to Section "Device":
Option "noAccel" "true"
Option "RenderAccel"  "false"
Option "MergedFB"  "off"

I am using an ATI Radeon 9800, TURION 64

i found this solution in another thread... i believe there were other changes for those using nvidia.

---

### Post by Nubsauce on 2005-08-18
[QUOTE=jamesrw]i fixed the problem by commenting out this line in Section "Module":
#     Load   "dri"

and added the following lines to Section "Device":
Option "noAccel" "true"
Option "RenderAccel"  "false"
Option "MergedFB"  "off"

I am using an ATI Radeon 9800, TURION 64

i found this solution in another thread... i believe there were other changes for those using nvidia.[/QUOTE]
 started in recovery mode, did rmmod nvidia rmmod -f sis_agp

modprobe nvidia

loaded agpgar and the nvidia driver..  Did startx worked fine.

Before it would hang on startup loading modules for X..

Never happened on the AMD64 Ubuntu versions with NVidia installed..

Just the i386 versions..

Also note, I commented out the dri module in the xorg.conf file.

I am going to try with that enabled as some systems I've used have kept that enabled..  heh

Regards

---

### Post by Nubsauce on 2005-08-19
Alright, after I did that, I experienced the locking up after two/three minutes..

I then added back in dri into xorg.conf

Then I added

NvAGP   "2"
RenderAccel "True"
NoLogo "True"


To my nvidia settings in the xorg.conf file.

I blacklisted sis_agp and agpgart from loading at boot, agpgart still loaded for some reason but after that, I had my 3d acceleration working and I had freed myself from the lockup after boot.

I am getting ready to redo the process again so if I missed a step, I'll edit this one with what I changed.  Hopefully this will at least work for your NVidia people as it worked for me.

Regards

---

### Post by mr_teal on 2005-12-13
I experienced the same problem and fortunately I solved it...
The problem seems to be the video device driver: the installation automatically found a video card "Ati" (that is correct) but used the driver "radeon", which definitely doesn't work with my hardware (ATI readeon X550). I tried to install the correct drivers (you can download them from ATI website [www.ati.com):](www.ati.com):) they come with a cute visual installer which is supposed to work both in X and in console mode... Unfortunately the console mode didn't work. I found out that the "vesa" driver at least works and let me see X (set "vesa" instead of "radeon" or "ati" or whatever in your video device section of your /etc/X11/xorg.conf). Then I started the graphical installer and it was easy.
Enjoy.

---

### Post by xvolks on 2005-12-18
Hi,

I have the same problem, seems to be related with KDE and SMP.

I am currentely running  2.6.15-rc5-ubuntu1mdt (SMP enable) with xfce4 (started with startx command) : everything is OK.

If I switch back to KDE, the computer hangs...

I have a P4C800-E deluxe Bios 1019
P4 3G
1 G RAM
ATI RADEON 7000

Edit : Up to date Kubuntu Dapper Drake !

# lspci
0000:00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
0000:00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
0000:02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller (LOM)
0000:03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by xvolks on 2005-12-18
Hi,

With the same kernel KDE works very well by changing one entry in /etc/X11/xorg.conf (commented out Load dri)

I have changed :
```

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection


```

To :
```

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection


```

---

### Post by duffydack on 2006-01-05
for me its any distro with a kernel newer than 2.6.10 using 686-smp anf HT enabled.  Lags like hell.  slow booting, apps using 98% cpu.   If Hoary got some of the newer apps and kde 3.5 in its repo`s i`d use that as its fine with its kernel.

---

### Post by Simon80 on 2006-01-25
[QUOTE=duffydack]for me its any distro with a kernel newer than 2.6.10 using 686-smp anf HT enabled.  Lags like hell.  slow booting, apps using 98% cpu.   If Hoary got some of the newer apps and kde 3.5 in its repo`s i`d use that as its fine with its kernel.[/QUOTE]
Have you tried using a kernel without smp? I've seen similar lagging issues on a Dell XPS that had an Intel EE in it, running FC4 (it wasn't mine :( ).  If that doesn't work, you can try compiling your own kernel as well, better than using an obsolete release.

---

### Post by hugelmopf on 2006-03-02
I am experiencing the same behaviour on a PC with two Athlon processors:
smp-kernel will crash within a few seconds of X startup.
nonsmp-kernel works fine.

Interestingly this also has a ATI Radeon graphics adapter, so maybe that is the problem's cause?

Edit: Nevermind about asking for a solution, I did not see the latest replies in this thread. Thanks.

---

### Post by Matt Yun on 2006-03-21
[QUOTE=duffydack]for me its any distro with a kernel newer than 2.6.10 using 686-smp anf HT enabled.  Lags like hell.  slow booting, apps using 98% cpu.   If Hoary got some of the newer apps and kde 3.5 in its repo`s i`d use that as its fine with its kernel.[/QUOTE]

My Supermicro P6DGS box  (dual PIII) also inexplicably hangs / freezes shortly after logging in, even via ssh.  Thanks to this thread and others, I know that it's not the video card (Voodoo4).  

I've been banging my head against this one since I installed Ubuntu 5.10.  Prior to that, the box had Kanotix 2005-03 on it, with a working Debian 2.6.10 smp kernel. Interestingly, I also tried Arch Linux on it last year, and it too would hang/freeze shortly after logging in.

Thanks, Duffydack, you provided some inspiration.  I am successfully running the 2.6.10-smp Ubuntu kernel from the Hoary repository.  I reinstalled with Hoary, installed the smp kernel, then changed the sources.list to Breezy and ran apt-get dist-upgrade.  Now I have a Breezy system, but I can still select the 2.6.10-smp kernel which is still retained through the dist-upgrade.

I tried just installing the 2.6.10-smp kernel from Breezy, but sysfs wouldn't mount the IDE drives properly (maybe because I'm using a SCSI drive for the root filesystem).  It was just quicker to install Hoary + smp kernel from scratch, then dist-upgrade to Breezy, than to figure out what was going wrong with sysfs.

Is there a bug report in Launchpad for this?

*Edit:* I just noticed this is a Hoary thread; my apologies in advance.

---

