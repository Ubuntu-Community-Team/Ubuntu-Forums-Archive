---
title: "Cannot enable visual effects"
date: 2010-02-22
forum: Desktop Environments
---

### Post by anur.bhargav on 2010-02-22
Hi everybody,
I am using Ubuntu 9.10. I have a problem with the visual effects. When I try to enable Visual Effects, it searches for some drivers and then gives this error, "visual effects could not be enabled".
This problem started when i uninstalled a driver by mistake(I suppose its the graphics driver)
My graphics card supports even the "extra" visual effects
These are the details when i typed the following command 
```
sudo lshw -C display
```
> bhargav@ubuntu:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:fdf00000-fdf7ffff ioport:ff00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fdb00000-fdbfffff


PLEASE HELP!!:(

---

### Post by prshah on 2010-02-23
> **anur.bhargav said:**
> "visual effects could not be enabled".
when i uninstalled a driver
(I suppose its the graphics driver)


The G33 chipset is supported by the "intel" driver. I doubt you would have uninstalled this, but if you have, you can easily reinstall it with ```
sudo apt-get install --reinstall xserver-xorg-video-intel
```

Then, delete (or move) any existing xorg.conf file and restart the X-server. To do this, open a virtual terminal (Ctrl+Alt+F1), login and give the commands```
sudo mv /etc/X11/xorg.conf ~
sudo service gdm restart
``` If your GUI does not appear, switch manually to the GUI terminal with Ctrl+Alt+F7 (or F8 ). If you get any errors, please post back with details.

---

### Post by anur.bhargav on 2010-02-23
> **prshah said:**
> The G33 chipset is supported by the "intel" driver. I doubt you would have uninstalled this, but if you have, you can easily reinstall it with ```
sudo apt-get install --reinstall xserver-xorg-video-intel
```

Then, delete (or move) any existing xorg.conf file and restart the X-server. To do this, open a virtual terminal (Ctrl+Alt+F1), login and give the commands```
sudo mv /etc/X11/xorg.conf ~
sudo service gdm restart
``` If your GUI does not appear, switch manually to the GUI terminal with Ctrl+Alt+F7 (or F8 ). If you get any errors, please post back with details.
Dear prshah,
I tried all the commands that u said.The first one seemed to work,it installed some package
But when i tried the next two i.e in the virtual terminal..
this command gave this message..
> bhargav@ubuntu:~$ sudo mv /etc/X11/xorg.conf ~
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory

I think u are right about me not uninstalling the driver , may be there's something else that i might have done.
My problem still 'stands'.Help please!

---

### Post by prshah on 2010-02-23
> **anur.bhargav said:**
> 
this command gave this message..

That message is normal, you can ignore it.

What happened with the "gdm restart" command?

---

### Post by anur.bhargav on 2010-02-23
> **prshah said:**
> That message is normal, you can ignore it.

What happened with the "gdm restart" command?
I'm am very sorry, I also did that ..but it din't change anything.. the problem still persists
It all started when i uninstalled CompizConfig Settings manager..Everything was fine until then..
When i uninstalled CompizConfig ,the dialog box showed two programs(Thats why i thought it might be a driver) .. I din't note down what the other program was and i just went ahead and uninstalled..
I've messed up.:(

---

### Post by prshah on 2010-02-23
> **anur.bhargav said:**
> 
When i uninstalled CompizConfig

...maybe you uninstalled compiz as well (can it be done?) In any case, open an emulated terminal (Applications-Accessories-Terminal) and give the following command, then please post back any output```
compiz --replace
```

---

### Post by anur.bhargav on 2010-02-23
> **prshah said:**
> ...maybe you uninstalled compiz as well (can it be done?) In any case, open an emulated terminal (Applications-Accessories-Terminal) and give the following command, then please post back any output```
compiz --replace
```
This is what i got
> bhargav@ubuntu:~$ compiz --replace
aborting and using fallback: /usr/bin/metacity 

---

### Post by gatorbrit on 2010-02-23
I have the same problem, but I think it is because my graphics card cannot handle compiz, so it defaults to the more basic metacity.  I could be wrong of course!

---

### Post by prshah on 2010-02-24
> **anur.bhargav said:**
> This is what i got
bhargav@ubuntu:~$ compiz --replace
aborting and using fallback: /usr/bin/metacity

Is that all you got? Or have you sanitized (removed) some portion of the output? Please post the entire output if it is edited.

Also, please post the output of the following commands as well```
cat /var/log/Xorg.0.log|grep -i -E driver\|exa\|uxa\|xaa
```

---

### Post by anur.bhargav on 2010-02-24
> **prshah said:**
> Is that all you got? Or have you sanitized (removed) some portion of the output? Please post the entire output if it is edited.

Also, please post the output of the following commands as well```
cat /var/log/Xorg.0.log|grep -i -E driver\|exa\|uxa\|xaa
```

Dear prshah,

Hi!I did not edit the output of the previous command i.e```
compiz --replace
```
In fact when i tried it out,the terminal started to behave weird..it din't close when i tried to close(I've attached a screenshot of the terminal).It din't even return to "bhargav@ubuntu:~$"

The output of the command ```
cat /var/log/Xorg.0.log|grep -i -E driver\|exa\|uxa\|xaa
``` is here
> bhargav@ubuntu:~$ cat /var/log/Xorg.0.log|grep -i -E driver\|exa\|uxa\|xaa
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
		Driver	"intel"
		Driver	"i810"
		Driver	"vesa"
		Driver	"fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): Using exact sizes for initial modes
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UXA(0): Driver registered support for the following operations:
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
bhargav@ubuntu:~$ 


---

