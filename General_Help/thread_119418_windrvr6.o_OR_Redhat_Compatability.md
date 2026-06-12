---
title: "windrvr6.o OR Redhat Compatability"
date: 2006-01-19
forum: General Help
---

### Post by Zxaos on 2006-01-19
Hey all, I'm just looking for some advice. I've got a program that is designed to run on an Redhat system (Xilinx ISE Webpack 8.1), and it installs fine, except for a section which controls USB drivers (needed to program FPGA boards). At this point, it spits out an error saying that /lib/modules/misc/windrvr6.o is has an invalid module format.

Can anyone shed some light on this for me?

---

### Post by xylometazolin on 2007-11-28
This error is thrown if the module is not compatible with your kernel, for example if your kernel was compiled with gcc-3.3 and the module was compiled with gcc-4.0.

Looks like you have to compile the module at your own. In this case I suggest you to use an alternative open source driver instead of the Xilinx driver, because the installation of the alternative driver is **much** easier and faster.

Here you can find a good guide:
- [https://wiki.kip.uni-heidelberg.de/KIPwiki/index.php/EDV:Xilinx-USB-Treiber](https://wiki.kip.uni-heidelberg.de/KIPwiki/index.php/EDV:Xilinx-USB-Treiber)
- some useful hints: [http://stefan.endrullis.de/en/xilinx_ise_8.2_ubuntu.html](http://stefan.endrullis.de/en/xilinx_ise_8.2_ubuntu.html)

---

