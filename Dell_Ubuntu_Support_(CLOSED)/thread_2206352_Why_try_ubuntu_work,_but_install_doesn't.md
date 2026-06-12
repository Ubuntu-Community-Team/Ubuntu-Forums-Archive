---
title: "Why try ubuntu work, but install doesn't"
date: 2014-02-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yan_solo on 2014-02-18
I have an Dell inspiron 5101. On 12.04 or right now 13.10 Why try ubuntu work, but install doesn't. I get vertical lines. 

I got it to install with acpi=off, and NOMODESET itès kinda slow, 
acpi=off  does it mean I can't install Ubuntu/incompatible?

---

### Post by grahammechanical on 2014-02-18
> [COLOR=#000000]does it mean I can't install Ubuntu/incompatible?[/COLOR]

No. When we use Try Ubuntu the live session runs with an open source video driver called Nouveau. When we install and tick "Install Third Party Software" a proprietary video driver is installed and it could be an incompatibility between your video graphic adapter and the proprietary video driver that is causing a problem when you rebooted.

When we install with NOMODESET then Ubuntu loads without setting a video mode. It could be that your system is running on llvmpipe. It is used as a fallback mode for graphic adapters that cannot run accelerated 3D graphics. It is being used because of using NOMODESET. And yes it does run kind of slow but it gets us to a desktop.

I suggest that you go to System Settings>Software and Updates>Additional Drivers tab and allow Ubuuntu to search for video drivers. You can then experiment. You will find Nouveau listed as well as a few versions of the proprietary video driver.

If you change video drivers and re-boot but do not get to a desktop, then reboot and at the Grub menu open the Advanced Options sub-menu and select Recovery Mode. Then select Resume. That should load to a desktop using llvmpipe again. Then you can experiment with video drivers once more.

Regards.

---

### Post by yan_solo on 2014-02-18
Thanks, I did not found any drivers in the add driver.

---

### Post by varunendra on 2014-02-19
Make sure you have done an "Update" (via gui, or via command - "sudo apt-get update") before checking the "Additional Drivers".

Also -
> **yan_solo said:**
> I got it to install with acpi=off, and NOMODESET itès kinda slow, 
**[COLOR="#FF0000"]acpi=off[/COLOR]**  does it mean I can't install Ubuntu/incompatible?
acpi=off should be last resort, when other **[boot options]("https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options")** don't help, as mentioned in the first post **[here]("http://ubuntuforums.org/showthread.php?t=1613132")**.

May we see a detailed list of your hardware? To post it, please open a terminal (Ctrl-Alt-T) and run the following command in it -
```
sudo lshw -numeric -sanitize > Desktop/lshw.txt
```
This will create a file named "lshw.txt" on your desktop. Either attach this file or copy-paste its contents in your next post so we can see what hardware you have and what proprietary drivers you need, if any.

---

### Post by yan_solo on 2014-02-19
Here is the file.

*-display UNCLAIMED
                description: VGA compatible controller
                product: RS482M [Mobility Radeon Xpress 200] [1002:5975]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
                physical id: 5
                bus info: [EMAIL="pci@0000:01:05.0"]pci@0000:01:05.0[/EMAIL]
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:c8000000-cfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff

---

### Post by varunendra on 2014-02-20
Your graphics card is this -
```
*-display **[COLOR="#FF0000"]UNCLAIMED[/COLOR]**
                description: VGA compatible controller
                **product: RS482M [[COLOR="#FF0000"]Mobility Radeon Xpress 200[/COLOR]] [[COLOR="#FF0000"]1002:5975[/COLOR]]**
                vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:c8000000-cfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff
```
But it should be well supported by the native "**radeon**" driver, as per the "**[Fully Supported]("https://help.ubuntu.com/community/RadeonDriver#Fully_Supported")**" cards list on the "[Radeon Driver]("https://help.ubuntu.com/community/RadeonDriver")" wiki page. Among others, it includes this -
> **[COLOR="#FF0000"]RS400[/COLOR]/RS480                 [COLOR="#FF0000"]Radeon XPRESS 200(M)[/COLOR]**/1100 IGP

It means you shouldn't have needed the "nomodeset" option. Try removing it from wherever you have added it, then reboot to see if you get better graphics and faster performance.

---

### Post by yan_solo on 2014-02-21
To remove the nomo, I donèt know how. I checked the box when I installed it.

If it is possible to test it. Like editing the grub. BUt i don't know what he mean by
'Add your boot option before these key words'

I found this
[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

Find the line ending with quiet splash. Add your boot option before these key words - i.e. so the line looks like [...]nomodeset quiet splash

---

### Post by mastablasta on 2014-02-21
this is chip is supported but not well. it is not a stellar chip bu ti htink people reported it works well under winxp.

anyway as for nomodeset you would need to get it into grub config i believe. it is described more in details here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
scroll down to: [B]Changing boot options Permanently for an Existing Installation

[/B]nomodeset is sometimes needed even if card is in supported list. i knwo i need ot add it for radeon hd 3650. don't know why exactly...

---

### Post by bapoumba on 2014-02-24
Moved to Dell as requested by the OP.

---

### Post by vishnuugopi on 2014-02-24
I have got the same laptop and you justhave to keep trying and it works

---

### Post by yan_solo on 2014-02-24
I had no luck with the repair. I tryed to remove the nomodeset, and I got the vertical lines again. It's installed, it's working. But it's really slow, I would need to know how to change the driver to one more appropriate.

---

