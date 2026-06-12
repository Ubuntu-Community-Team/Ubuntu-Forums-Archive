---
title: "Display problems, Need Drivers Maybe?"
date: 2015-01-07
forum: Desktop Environments
---

### Post by gabmuks on 2015-01-07
I have a nividia graphics board installed. Is there a way to install nividia drivers?

Strange thing is, my monitor is plugged directly into graphics card, and yet
Ubuntu does not identify it as a Nividia card.

The display is "sqeezed" in on both sides. That is the best way to describe it.
Have tried adjusting the monitors onboard adjustments, but that didn't help.

I have Windows 7 installed side by side with Ubuntu 14. The display works great
with Windows but not with the Ubuntu.

Any ideas??

---

### Post by gabmuks on 2015-01-07
I just realized I've installed a 32 bit Ubuntu version on my 64 bit computer.

Could that be the problem??

---

### Post by Bashing-om on 2015-01-07
gabmuks; Welp.

Unless you have greater than 3 Gigs of ram, the 32 bit OS will run a bit faster on the 64 bit hardware ( addressing) .

So, let us look at the graphics situation. 
Post back - Between Code Tags - the outputs of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Which will identify your graphics card(s) and if/what driver is loaded .
Then perhaps a change in drivers is in order .

[INDENT][INDENT]a tale in the telling
[/INDENT][/INDENT]

---

### Post by gabmuks on 2015-01-07
Thanks for reply. Sorry for delay.
Was plowing snow.
When I look in "settings" in Ubuntu, after GRAPHICS, it says: Gallium 0.4 on NVA8

Here is results of your commands:

```
  -HP-Compaq-dc5800-Microtower:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 210] [10de:0a65] (rev a2)
    Kernel driver in use: nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
    Kernel driver in use: snd_hda_intel
liz@liz-HP-Compaq-dc5800-Microtower:~$ sudo lshw -C display
                  
```

---

### Post by Bashing-om on 2015-01-07
gabmuks; Hey ...

No output from " sudo lshw -C display " ?
Thus far it appears you are running with the open source driver, nouveau. I wonder what is going on that the display is not detected properly ?
The card and display are 2 different components, and the 'driver' is that link between the card, the monitor and the kernel.

Give the system some time to look at the hardware and what it detects for the related drivers.

That card - [GeForce 210] is supported. And in the "Additional drivers" utility, I would expect it to find the 304.xx version of the proprietary driver .. and if desired to install it.

[INDENT][INDENT]sometimes, one has to give the kernel a helping hand
[/INDENT][/INDENT]

---

### Post by gabmuks on 2015-01-07
Almost forgot this part:

```
  *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:45 memory:f2000000-f2ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:1100(size=128) memory:f3080000-f30fffff
  
```

---

### Post by Bashing-om on 2015-01-07
gabmuks; well ---

The output from 'lshw' looks good to me.

What is the result when you install a proprietary driver from the "Additional Drivers" utility ?

[INDENT][INDENT]maybe then yes 
[/INDENT][/INDENT]

---

### Post by gabmuks on 2015-01-07
Here is results of commands with proprietary driver installed:

```
 liz@liz-HP-Compaq-dc5800-Microtower:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 210] [10de:0a65] (rev a2)
    Kernel driver in use: nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
    Kernel driver in use: snd_hda_intel
liz@liz-HP-Compaq-dc5800-Microtower:~$ sudo lshw -C display
[sudo] password for liz: 
  *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:45 memory:f2000000-f2ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:1100(size=128) memory:f3080000-f30fffff
liz@liz-HP-Compaq-dc5800-Microtower:~$ 
 
```

The display is still "sqeezed" so to speak, but at least it doesn't disintegrate into pixels every 5 seconds like before.
So the Nvidia driver helped in that respect.

Could the sqeeze problem have something to do with using the HDMI output from the video card?

---

### Post by Bashing-om on 2015-01-07
gabmuks; Humm ...

> 
Could the sqeeze problem have something to do with using the HDMI output from the video card?


I would think that is all proper, the monitor is HDMI cabable, yes ?

Might see what positive results you can obtain tweaking from "nvidia-settings" , now that you have the Nvidia driver installed.

[INDENT][INDENT]it's a thought
[/INDENT][/INDENT]

---

### Post by gabmuks on 2015-01-08
That was it!! Thanks much!

I changed the resolution in the Nvidia Settings
and problem solved.

I will mark thread solved.

Thanks again.

---

### Post by Bashing-om on 2015-01-08
gabmuks; Great !

Pleased it worked out.
Simpler things 1st .

[INDENT][INDENT]ain't 'buntu wonderful
[/INDENT][/INDENT]

---

