---
title: "How can I save the screen resolution?"
date: 2009-05-24
forum: General Help
---

### Post by rost78 on 2009-05-24
Hello,

My installation of Xubuntu 9.04 was successful and so far I'm very pleased by the clean look. However, there is a problem with the screen resolution.. I've set the resolution to 1280x960 via the Settings panel but as soon as I log out, the resolution is reset to 800x600.

By the way, I'm running Xubuntu as a virtual machine in VMware Workstation 6.5.

Can anybody help me?

Thanks,

Robert

---

### Post by kerry_s on 2009-05-24
i been looking for that 1 to. :lolflag:

I've manually put it in to xorg.conf for the time being to get the size i want.

press alt+f2
type> **gksudo mousepad /etc/X11/xorg.conf**

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	DefaultDepth	24
        SubSection "Display"
                Viewport   0 0
                Depth     24
		Modes     "1280x960"
        EndSubSection
EndSection
```

mine looks like this for me:

---

### Post by Girl™ on 2009-05-24
> **rost78 said:**
> 
By the way, I'm running Xubuntu as a virtual machine in VMware Workstation 6.5.


This might be a long shot, but have you installed VMWare Tools?

---

### Post by rost78 on 2009-05-24
> **Girl™ said:**
> This might be a long shot, but have you installed VMWare Tools?
 
Yes, VMware Tools are installed and running. However, when starting the configuration of the tools, a message like "X configuration skipped as no X drivers detected" comes up. This didn't cause the descrbed behavior in other versions like Ubuntu or Kubuntu.

---

### Post by rost78 on 2009-05-25
> **kerry_s said:**
> I've manually put it in to xorg.conf for the time being to get the size i want.
 
Doesn't work in my case :(

---

### Post by kerry_s on 2009-05-25
> **rost78 said:**
> Doesn't work in my case :(

yeah, i missed that vmware part.
not sure if will help but when i used virtualbox, to get a certain screen size i had to add a console screen size to grub. example: vga=791, which would give 1024x768. 

```

Screen   640x480     800x600     1024x768     1280x1024     1600x1200
Colors    ----------------------------------------------------------------------
 256       | 769             771             773           775               796
 32,768  | 784              787            790           793               797
 65,536  | 785              788            791           794               798
 16.8M    | 786             789             792           795               799 

```

---

### Post by rost78 on 2009-05-30
This doesn't work either :( I'm really asking myself about the difference between an installation of Xubuntu or Ubuntu. Can't figure it out...

---

