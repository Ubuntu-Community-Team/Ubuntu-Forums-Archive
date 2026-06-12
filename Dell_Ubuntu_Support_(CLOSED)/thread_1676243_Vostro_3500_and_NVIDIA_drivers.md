---
title: "Vostro 3500 and NVIDIA drivers"
date: 2011-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cdesseno on 2011-01-26
I just bought a new DELL Vostro 3500 which has an NVIDIA 310M graphic card integrated. Although by default Ubuntu uses the *nouveau* drivers for video and they are working fine (but no for 3D aceleration, obviously) I tried to install the official NVIDIA drivers but I failed each time.

I tried everything: downloading from Jockey, downloading and installing differents versions from Nvidia's website, etc... Each time I rebooted the black screen appeared again, so I had to restart in safe mode, delete the *xorg.conf* and *sudo dpkg-reconfigure xserver-xorg*.

Anyone has a solution? Else I'll keep on searching about this every day :(

---

### Post by mikewhatever on 2011-01-26
Try running nvidia-xconfig from the recovery mode after installing the driver.

---

### Post by Ondrejicek on 2011-01-27
Dell Vostro 3500 has two graphics card. One is Nvidia 310M and the other is integrated into core i5 processor. I believe you are using the Intel one (default), although you have nouveau driver loaded. I don't think there is any solution at this moment how to run proprietary nvidia drivers.

It should be possible to disable Intel GPU and use Nvidia, but only with nouveau. But I didn't have much luck with this so far. I've tried solution for Vostro 3700, but didn't worked for me. If anyone knows how to set up nouveau on 3500, please tell. Thanks.

---

### Post by cascade9 on 2011-01-27
> **Ondrejicek said:**
> It should be possible to disable Intel GPU and use Nvidia, but only with nouveau. But I didn't have much luck with this so far. I've tried solution for Vostro 3700, but didn't worked for me. If anyone knows how to set up nouveau on 3500, please tell. Thanks.

If you can disable the Intel card in the BIOS, then the nvidia drivers will work. (not many nvidia optimus laptops have that option though). 

If by 'disable' intel you mean blacklisting it, or something like that.....maybe then you could only use nouveau. IMO the nvidia drivers should work if that worked (which as far as I know it doesnt)

---

### Post by cdesseno on 2011-01-27
> **cascade9 said:**
> If you can disable the Intel card in the BIOS, then the nvidia drivers will work. (not many nvidia optimus laptops have that option though). 

If by 'disable' intel you mean blacklisting it, or something like that.....maybe then you could only use nouveau. IMO the nvidia drivers should work if that worked (which as far as I know it doesnt)

I checked the BIOS settings and I didn't find any option to disable the integrated graphics card.

---

### Post by realzippy on 2011-01-27
> **cdesseno said:**
> I checked the BIOS settings and I didn't find any option to disable the integrated graphics card.

So welcome to the Nvidia Optimus trap...!!

The worst thing is that the nvidia card still sucks battery power and cannot be switched off.So an optimus laptop is nearly useless without power supply.Bring it back to the store and change it to an ATI graphics laptop...
and send NVIDIA a note about this...

---

### Post by Ondrejicek on 2011-01-27
I've just successfuly enabled Nvidia with nouveau using this tutorial:

[https://bbs.archlinux.org/viewtopic.php?pid=882737#p882737]("https://bbs.archlinux.org/viewtopic.php?pid=882737#p882737")

If you want to use Intel card only, you can disable nvidia by running these commands at startup:

modprobe acpi_call
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

I tried it on Arch linux, but it will probably work on Ubuntu too.

---

### Post by cdesseno on 2011-01-27
> **Ondrejicek said:**
> I've just successfuly enabled Nvidia with nouveau using this tutorial:

[https://bbs.archlinux.org/viewtopic.php?pid=882737#p882737]("https://bbs.archlinux.org/viewtopic.php?pid=882737#p882737")

If you want to use Intel card only, you can disable nvidia by running these commands at startup:

modprobe acpi_call
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

I tried it on Arch linux, but it will probably work on Ubuntu too.

Thank you! I'll check it out.

[Here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/643895") is the actual bug submitted by another to Launchpad.

---

### Post by realzippy on 2011-01-28
From [https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)  :

[I]One of the hybrid-graphics-linux Launchpad team members has created a Linux kernel module to call ACPI methods through /proc/acpi/call. The code is here:
[http://github.com/mkottman/acpi_call](http://github.com/mkottman/acpi_call)
You can try it by installing the module and calling it like this:[/I]
```
git clone http://github.com/mkottman/acpi_call.git
cd acpi_call
make
sudo insmod acpi_call.ko
./test_off.sh
```
[I]If you see a "works!" message, it's working. On an unplugged laptop, clicking on the battery indicator before and after running the test.sh script, should show a difference of about an extra 1-3 hours battery 
life.[/I]

I get
```
me@hmine:~/acpi_call$ ./test_off.sh
Trying \_SB.PCI0.P0P1.VGA._OFF: failed
Trying \_SB.PCI0.P0P2.VGA._OFF: works!

```

Unfortunately there is no increasing battery capacity,nvidia card still sucking power and
```
dmesg | grep -i VGA
```
shows
```
[    0.000000] Console: colour VGA+ 80x25
[    1.472055] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.472063] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    1.472068] vgaarb: loaded
[   18.538784] VGA switcheroo: detected DSM switching method \_SB_.PCI0.P0P2.VGA_ handle
[   18.691218] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   18.691221] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   19.733606] ACPI Warning for \_SB_.PCI0.P0P2.VGA_._DOD: [COLOR="Red"]Return type mismatch - found Integer, expected Package (20100428/nspredef-1053)[/COLOR]
[   20.031598] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[  127.669855] acpi_call: Calling \_SB.PCI0.P0P1.VGA._OFF
[  127.671221] acpi_call: Calling \_SB.PCI0.P0P2.VGA._OFF


```

Any ideas concerning:
```
Return type mismatch - found Integer, expected Package (20100428/nspredef-1053)
``` ?

---

### Post by cdesseno on 2011-01-30
I have posted a thread in the NVIDIA forums, please add your comments there so we can get an official reply: [http://forums.nvidia.com/index.php?showtopic=192023]("http://forums.nvidia.com/index.php?showtopic=192023")

---

### Post by realzippy on 2011-01-30
It is not a bug,NVIDIA currently has no intention to make hybrid graphics
work in linux,as [Aaronp said in the NVlinuxforum]("http://www.nvnews.net/vbulletin/showthread.php?t=144750"),where certain thread exists about this.
The guys at launchpad bug#643895 took a while to realise that their problems are due to optimus technology.
There is no sense in complaining unless you find 10.000 optimus victims who
sign up a note.

---

### Post by cdesseno on 2011-02-04
I realized that now I can't change the *Visual Effects* to *Normal* or *Extra*. Before trying to install the Nvidia drivers (with default video configuration) the *Visual Effects* were on *Normal*. Furthermore I can't run 3D screensavers.

What libraries I have to reinstall? There is any way to go back to the default video configuration (tried with sudo dpkg-reconfigure xserver-xorg, no results)? Also tried reinstalling xserver-xorg and mesa libraries...

---

### Post by realzippy on 2011-02-05
First make sure you deleted xorg.conf

```
sudo rm /etc/X11/xorg.conf

```
Reboot.Still not working?:

If installed with jockey try reinstalling:

xserver-xorg-video-nv
xserver-xorg-video-intel
xserver-xorg-video-nouveau
xserver-xorg-video-vesa


If installed manually run the NVIDIA installer with --uninstall option:

```
sudo sh NVIDIA* --uninstall
```

---

### Post by cdesseno on 2011-02-05
> **realzippy said:**
> First make sure you deleted xorg.conf

```
sudo rm /etc/X11/xorg.conf

```
Reboot.Still not working?:

If installed with jockey try reinstalling:

xserver-xorg-video-nv
xserver-xorg-video-intel
xserver-xorg-video-nouveau
xserver-xorg-video-vesa


If installed manually run the NVIDIA installer with --uninstall option:

```
sudo sh NVIDIA* --uninstall
```

Tried all but it continues as always and actually I have no xorg.conf.
In the live CD the *Visual Effects* are working, may be I can copy some kind of configuration.

---

### Post by realzippy on 2011-02-05
Are libGL.so and libglx.so ok?
/usr/lib/xorg/modules/extensions should contain:
libdbe.so  libdri2.so  libdri.so  libextmod.so  libglx.so  librecord.so

Try reinstalling
libgl1-mesa-glx
libgl1-mesa-dri
xserver-xorg-core

---

### Post by cdesseno on 2011-02-05
> **realzippy said:**
> Are libGL.so and libglx.so ok?
/usr/lib/xorg/modules/extensions should contain:
libdbe.so  libdri2.so  libdri.so  libextmod.so  libglx.so  librecord.so

Try reinstalling
libgl1-mesa-glx
libgl1-mesa-dri
xserver-xorg-core

Thanks for your fast response! I followed your steps but it is like before :(.

---

### Post by realzippy on 2011-02-05
Sorry I am out.Desperate attempt:

Add xswat ppa.Update,upgrade,hope... that it also checks modules/libs.
Also run their drivers for testing although the default ran ok..

Edit;
While checking my xswat packages noticed that those might also be relevant to you:
libdrm-intel1
libdrm2
libkms1
libdrm-dev
intel-gpu-tools

Btw,did you disable any modules while manually nvidia install attempts you formerly made?

---

### Post by cdesseno on 2011-02-06
> **realzippy said:**
> Sorry I am out.Desperate attempt:

Add xswat ppa.Update,upgrade,hope... that it also checks modules/libs.
Also run their drivers for testing although the default ran ok..

Edit;
While checking my xswat packages noticed that those might also be relevant to you:
libdrm-intel1
libdrm2
libkms1
libdrm-dev
intel-gpu-tools

Btw,did you disable any modules while manually nvidia install attempts you formerly made?

Again, it is like before, it is not working.
How can I check what video driver I am using? (I have no xorg.conf)

Thanks!

---

### Post by realzippy on 2011-02-06
```
lspci -v
```

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 0488
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d1400000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4050 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	[COLOR="SeaGreen"]Kernel driver in use: i915[/COLOR]
	Kernel modules: i915

---

### Post by realzippy on 2011-02-06
Btw,what does compiz "say" when started from the terminal?

```
compiz --replace
```

---

### Post by cdesseno on 2011-02-06
> 01:00.0 VGA compatible controller: [COLOR="Red"]nVidia Corporation GT218 [GeForce 310M][/COLOR] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 044e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at fa000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: [COLOR="Red"]nouveau[/COLOR]
	Kernel modules: nouveau, nvidiafb

It seems it is trying to use de 310M :/

With compiz (no errors):

> carlos@carlos-vostro:~$ compiz --replace

Launching fallback window manager

---

### Post by realzippy on 2011-02-06
...so how did you manage to turn off the intel card?

What is the output from liveCD ?

......................................................

Launching fallback window manager 
is an error,,,compiz does not start.

---

### Post by realzippy on 2011-02-06
Have you ever run W7 on this laptop with both graphics?

---

### Post by cdesseno on 2011-02-06
My error (I didn't see the other VGA):
With Ubuntu installed:
> 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 044e
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at fa400000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f080 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 044e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at fa000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb



With live CD:
> 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 044e
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at fa400000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f080 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 044e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at fa000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb



Yes, I have dual boot with WIN7 which is working ok with the NVidia drivers (optimus).

---

### Post by realzippy on 2011-02-06
```
lshw -C Display
```
what does "configuration" line say? (each card)...

---

### Post by cdesseno on 2011-02-06
Here it is:
>   *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 310M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
[COLOR="Red"]       configuration: driver=nouveau latency=0[/COLOR]
       resources: irq:16 memory:f9000000-f9ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fa000000-fa07ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
[COLOR="Red"]       configuration: driver=i915 latency=0[/COLOR]
       resources: irq:48 memory:fa400000-fa7fffff memory:b0000000-bfffffff ioport:f080(size=8)

---

### Post by realzippy on 2011-02-06
No idea what happened.
you could go on and load/unload modules,use an xorg.conf to force intel, but if it worked formerly, a fresh install might have been faster..

---

### Post by cdesseno on 2011-02-06
Ok.. anyway, thanks! I'll try to search a xorg.conf.

---

### Post by realzippy on 2011-02-06
# minimal xorg.conf file.Works here on optimus..
```
Section "Monitor"
	Identifier   "Configured Monitor"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

```

---

### Post by cdesseno on 2011-02-06
I made *Xorg -configure* and later a copy of the file created to /etc/X11/xorg.conf, now the visual effects are working. :)::confused:

---

