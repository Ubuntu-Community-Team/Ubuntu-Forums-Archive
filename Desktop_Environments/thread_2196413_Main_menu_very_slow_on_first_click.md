---
title: "Main menu very slow on first click"
date: 2013-12-29
forum: Desktop Environments
---

### Post by yoramdavid on 2013-12-29
Hello all,

I have Ubuntu 12.04 in fallback mode and the Main menu is very slow to open on the first click.
I am not talking about ms, but about s: it takes about 5 seconds to open.
It is that bad that I normally click on it, go do something else while it opens.

Is there any work around to speed-up the menu?

Thanks.
Happy 2014

---

### Post by ajgreeny on 2013-12-29
Just as a trial try making a file with this content in your home folder called **.gtkrc-2.0** (note the . at the start of the filename) and then logout and login again, or as a better test restart.

```
# This file should be placed in your (x)ubuntu home folder
# and name ".gtkrc-2.0"
#
gtk-menu-popup-delay=0
gtk-menu-popdown-delay = 0
gtk-menu-bar-popup-delay = 0
gtk-enable-animations = 0
gtk-timeout-expand = 10

```

---

### Post by yoramdavid on 2013-12-29
Thanks  ajgreeny's.

That made a difference, now menu opens after one second, more or less.
I assume it is not possible to have it to open instantly, so I will mark this threat as solved?

Regards,

Yoram

---

### Post by ajgreeny on 2013-12-29
What hardware do you have?  If it is rather old, and with a low spec graphic card, it may be that is the main cause of the slow opening menu.

---

### Post by yoramdavid on 2013-12-30
I must say it is much better now.
If it was due to a slow computer, then would it not be slow every time I press the menu?
After the first click, then it opens immediately.

I have 2GB Ram
Intel core 2 CPU 5500 @1.66Hz
Graphic card Nvidia GeForce Go 7400 256 MB Ram, GPU 100 MHz

---

### Post by ajgreeny on 2013-12-30
Are you running the open source or proprietary driver for the nvidia card?

---

### Post by yoramdavid on 2013-12-31
> **ajgreeny said:**
> Are you running the open source or proprietary driver for the nvidia card?

Thank you ajgreeny,

I am not sure about which one I have installed nor I do know how to check it out.
I am tempted to say I have the Proprietary drivers, but could not be sure.

I looked into the Nvidia X Sever Setting but I could not see anything saying which one is installed.
After some googling, I found a few commands of which I paste here the results:
```

yoram@yo-ii:~$ sudo lspci -k
[sudo] password for yoram: 
01:00.0 VGA compatible controller: NVIDIA Corporation G72M [GeForce Go 7400] (rev a1)
	Subsystem: Hewlett-Packard Company Device 30bb
	Kernel driver in use: nvidia
	Kernel modules: nvidia_304, nouveau, nvidiafb
```

```
yoram@yo-ii:~$ lspci  -mm | grep VGA
01:00.0 "VGA compatible controller" "NVIDIA Corporation" "G72M [GeForce Go 7400]" -ra1 "Hewlett-Packard Company" "Device 30bb"
```

```
yoram@yo-ii:~$ sudo lshw -C display ; dpkg -l | grep nvidia
  *-display               
       descrição: VGA compatible controller
       produto: G72M [GeForce Go 7400]
       fabricante: NVIDIA Corporation
       physical id: 0
       informações do barramento: pci@0000:01:00.0
       versão: a1
       largura: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuração: driver=nvidia latency=0
       recursos: irq:16 memória:dd000000-ddffffff memória:c0000000-cfffffff memória:dc000000-dcffffff
ii  nvidia-304                                    304.88-0ubuntu0.0.3                                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                                 1:0.2.44.2                                                Find obsolete NVIDIA drivers
ii  nvidia-current                                304.88-0ubuntu0.0.3                                       Transitional package for nvidia-current
ii  nvidia-settings-304                           304.88-0ubuntu0.0.3                                       Tool for configuring the NVIDIA graphics driver****
```

Greetings,

David

---

### Post by ajgreeny on 2013-12-31
Sorry but I have never had an nvidia card so have no way to help you here apart from saying that if you did not install the proprietary driver using the additional drivers utility, I think you will be using the open source driver.  However I note that the 
```
Kernel driver in use: nvidia
	Kernel modules: nvidia_304, nouveau, nvidiafb
```
which I think means you do have the nvidia proprietary driver

---

### Post by yoramdavid on 2014-01-01
> **ajgreeny said:**
> Sorry but I have never had an nvidia card so have no way to help you here apart from saying that if you did not install the proprietary driver using the additional drivers utility, I think you will be using the open source driver.  However I note that the 
```
Kernel driver in use: nvidia
	Kernel modules: nvidia_304, nouveau, nvidiafb
```
which I think means you do have the nvidia proprietary driver

That is OK.
During install I remember there was an option to allow install of proprietary drivers such as for mp3, graphic cards, etc.
According to [this]("http://www.google.pt/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CC8QFjAA&url=http%3A%2F%2Faskubuntu.com%2Fquestions%2F182640%2Fhow-do-i-know-if-im-running-the-open-source-amd-drivers-for-radeon&ei=I2LEUtqgKMHg7QbC04CIBQ&usg=AFQjCNGjU6M2DVb9XWmT6rgtBY_wnL2WRA&bvm=bv.58187178,d.ZGU") threat I just read, the proprietary driver is called 'nvidia' and the open source is called 'nouveau', I have both listed up there.

But I have the NVIDIA X Server Settings Gui with the options, so that also is an indication that the proprietary is installed if I understood correctly what I read on another post.

---

