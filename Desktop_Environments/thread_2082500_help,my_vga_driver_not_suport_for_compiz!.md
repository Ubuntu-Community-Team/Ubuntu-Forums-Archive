---
title: "help,my vga driver not suport for compiz!"
date: 2012-11-09
forum: Desktop Environments
---

### Post by geodeth on 2012-11-09
when I try to check compatibility vga I get the following message  :
rendy@rnd-rose:~$ sudo chmod +x compiz-check
[sudo] password for rendy: 
rendy@rnd-rose:~$ ./compiz-check
```
More than one graphics chip detected -- sorry, the script can not handle that.
 Aborting.
```~$ lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1058 (rev a1)
```~$ lshw -C video
```
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:db000000-dbffffff memory:c0000000-c7ffffff memory:c8000000-c9ffffff ioport:d000(size=128) memory:dc000000-dc07ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:52 memory:dc400000-dc7fffff memory:b0000000-bfffffff ioport:e000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```
im using ubuntu 12.10 and my vga its nvidia geforce 610m (notebook user)
pliz help that problem, how i can fix ore update driver vga.
couse im Newbie here.
thx before :)

---

### Post by grahammechanical on 2012-11-09
Why are do you want to check for Compiz compatibility? Ubuntu uses Compiz as the compositing/window manager. You would not have a working Ubuntu without Compiz compatibility.

I also think that you have Nvidia Optimus technology. You may need to read about it here:

[https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

Regards

---

### Post by geodeth on 2012-11-09
> **grahammechanical said:**
> Why are do you want to check for Compiz compatibility? Ubuntu uses Compiz as the compositing/window manager. You would not have a working Ubuntu without Compiz compatibility.

I also think that you have Nvidia Optimus technology. You may need to read about it here:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Regards
i just install  bumblebee project and i can use compiz?
wht are must do after that?
Regards

---

### Post by geodeth on 2012-11-10
some one help pliss...

---

### Post by grahammechanical on 2012-11-10
Please explain what you want to do. Ubuntu would not work without Compiz. So, you are using Compiz. What do you want to do that you think that you need Compiz to do it?

All video cards have VGA compatibility. It is a very old standard to give a basic video mode with whatever monitor is being used. To get better quality video displays we need special video drivers.

Ubuntu uses an open source video driver called Nouveau and sometimes we can install a proprietary driver from the company that made our video card. As far as I know Nvidia has only recently started working on a driver for its Optimus technology. So, Linux developers have tried to develop the Bumblebee project.

If you now have a suitable video driver for your machine, then you must tell us what the problem is. I do not know what you are wanting to do.

I can make three types of connection to my monitor. I can use VGA, DVI and HMDI. What is the difference?

Computers are digital devices. Early monitors used cathode ray tubes (CRT) and so were analogue devices. With a VGA connection the digital video information from the computer is first converted to analogue information so that the CRT monitor can display the information.

Modern (LED) monitors are digital devices. So, they can be connected directly to the digital video circuits of the computer without the need for conversion to analogue. This is what happens when we connect a  modern monitor to a computer using DVI. It does the same as VGA but without the conversion to analogue.

What happens if we connect a modern monitor to a computer using the VGA connection? The digital signal is first converted to analogue and then sent to the monitor where it is converted back to digital.

HDMI is the same as DVI but with the ability to use high definition video information.

I cannot think of any other way to help than the help I have given you.

Regards.

---

### Post by geodeth on 2012-11-11
couse i cant found icon for setting desktop cube,like this :
[spoiler][IMG]http://imageshack.us/a/img141/4067/screenshotfrom201211111.png[/IMG]
[/spoiler]
what i must do?

---

### Post by zombifier25 on 2012-11-11
Install the compiz-plugins-extra package. Then again, that probably won't work, read here for more details: [https://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/](https://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/)

---

