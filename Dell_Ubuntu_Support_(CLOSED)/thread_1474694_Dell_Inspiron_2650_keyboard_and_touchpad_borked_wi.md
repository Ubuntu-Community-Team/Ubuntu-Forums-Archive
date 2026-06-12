---
title: "Dell Inspiron 2650 keyboard and touchpad borked with Lucid"
date: 2010-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by afrodeity on 2010-05-06
I have had problems getting the right keymap for the Dell Inspiron 2650. Now the keyboard and touchpad totally borked. I tried booting up the installer and seeing if I can reinstall, but same problem with the installer.

This is not a mechanical defect since I can boot up a Puppy Linux live CD and the machine works fine. 

Problem is similar to this thread:
[http://ubuntuforums.org/showthread.php?t=1443535](http://ubuntuforums.org/showthread.php?t=1443535)

Could be the result of an update to xserver-xorg.

I have tried booting up in recovery mode, but when it reaches the recovery panel options are frozen.

Any workaround or solution? I really don't want to have to run another distro.

---

### Post by tfleonard on 2010-05-06
I had the same problem.  Add the following to your boot line:

acpi=off

You can do this manually from the grub menu to test it.   I have tried all of the other variations and it appears that acpi is broken in this version of the kernel for this machine.


As I mentioned in another post, your machine will boot and the keyboard/touch pad will work.  But, the battery status will not work and when you shut down you will have to push the power button to turn off the machine.  


TIm

---

### Post by afrodeity on 2010-05-07
can't edit grub. i cane shift into it, but e key frozen, up and down arrows ok. ouch.

---

### Post by LambdaCalculus379 on 2010-06-28
Same issue here. I have a Dell Inspiron 2650 that I want to install Lucid on for a family friend, but the keyboard and touchpad are borked. I can use a USB keyboard and mouse without issue, but I also want the laptop's keyboard and mouse working.

I don't have a wireless PCMCIA card, so I can't try wifi out.

Funny that Hardy (8.04) works just fine, but Lucid doesn't.

---

### Post by afrodeity on 2010-06-28
> **LambdaCalculus379 said:**
> Same issue here. I have a Dell Inspiron 2650 that I want to install Lucid on for a family friend, but the keyboard and touchpad are borked. I can use a USB keyboard and mouse without issue, but I also want the laptop's keyboard and mouse working.

I don't have a wireless PCMCIA card, so I can't try wifi out.

Funny that Hardy (8.04) works just fine, but Lucid doesn't.

been looking everywhere for an inspiron series laptop keymap 

found nada

apparently one can make one using a keydump

haven't been able to thus far

typing this on the inspiron which has feisty on it at the moment

seem to be downgrading

oh dear

---

### Post by amireldor on 2010-09-19
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727)

comment #93 this solved my problem (for now at least)
although i'm on hp dv6000

---

### Post by Cycledoc on 2010-09-19
I had a similar problem.  Changed the grub  boot menu (hitting e as booting up)

inserted "acpi=off" prior to quiet splash  (no quotes)

Everything works as tlleonard notes.  Makes the machine functional again.

good luck

---

### Post by orthello on 2010-10-18
Just to let everybody know:
Dell Inspiron 2650 keyboard/mousepad issue still exists in maverick meerkat.
Haven't tried the "acpi=off" trick during startup yet.

But I have accidentally managed to get everything to work by changing power management settings, using a USB mouse and reboot. This turned out to be a permanent fix/workaround. As far as can remember the laptop still powered down by itself when shutting down.

I'll investigate this further in a few days. Then I will also come up with the exact changes in power management. Because it was by accident, I don't exactly know any more what I did. *blush*

---

### Post by fari81 on 2010-10-25
Setting acpi=off in /etc/default/grub and then running update-grub worked. But as tfleonard has mentioned, the power button does not work anymore, and we need to manually power off the machine.

It would be great if we can find a real fix for this. 

The post by lousygarua is more about not having touchpad after logon. My problem is that I don't have access to neither keyboard nor touch pad even before logging in.

orthello: Have you figured out what you changed in power manager to get the machine working?

---

### Post by Cycledoc on 2010-10-28
I believe acpi controls power management so by turning it off the automatic off function ceases to work.  I haven't found a fix for that.

Am using my 2650 with Maverick with good results, though some problems with pulseaudio.

Not perfect but runs so much better than with Windows that I rarely use that OS--only to download audiobooks.

---

### Post by fari81 on 2010-10-28
Ok, we updated the bios and it worked perfectly (thanks to my colleague).

Here's the instructions:
[http://www.ubuntu-unleashed.com/2007/09/howto-easily-upgrade-dell-bios-in.html]("http://www.ubuntu-unleashed.com/2007/09/howto-easily-upgrade-dell-bios-in.html")

The method works except that the link to the bios file is wrong. It should be 
[http://linux.dell.com/repo/firmware/bios-hdrs/]("http://linux.dell.com/repo/firmware/bios-hdrs/")

---

### Post by bobmartens on 2010-11-01
Try adding "pci=noacpi", no quotes, after the quiet splash line. Worked for me. If this works, update grub in terminal.

---

