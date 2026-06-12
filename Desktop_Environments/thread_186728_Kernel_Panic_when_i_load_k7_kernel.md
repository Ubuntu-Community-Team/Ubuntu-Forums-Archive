---
title: "Kernel Panic when i load k7 kernel"
date: 2006-06-02
forum: Desktop Environments
---

### Post by lotv on 2006-06-02
I successfully installed i386 version Dapper (i had some problems with my ethernet and acpi both during the installation and when i tried to access the net afterwards, so i stopped loading acpi and acpi-support).

I have an athlon 64 cpu, and i installed the k7 server, but i get a kernel panic when i select this kernel from grub with the followin message

MP-BIOS bug 8254 timer not connected to IO-APIC (this also occurs with the i386 kernel, but it loads OK)
Kernel Panic non syncing : IO-APIC Timer doesn't work. Boot with apic=debug ans send report, try booting with the noapic option.

any ideas?

---

### Post by Roobert on 2006-06-16
I have no idea why it's happening, but I had the exact same error, and here's how I fixed it:

At the grub boot screen, use your arrow keys to highlight "kernel /boot/linuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash" (your exact paths and numbers might be a little dfferent). Then type 'e' to edit the boot options; you will be taken to another screen. Append 'noapic' to the end of the boot options, and hit enter. Then just type 'b' to boot. Dapper should then boot normally.

To make these changes permanent, do the following:



```
sudo gedit /boot/grub/menu.lst
```


and append 'noapic' to the line the says "#defoptions=", then

Code:

```
update grub
```


and reboot. I took this help info from another post, none of it is original, but if I find the original post where I dea this, I will link to it from here.

~ Eric.
__________________
Registered Linux User #402664

---

### Post by jgcamp99 on 2006-06-16
An Athlon 64 cpu (socket 754 or 939) is not a K7, socket 462 is K7, what you have is the 64 bit AMD K8. Your cpu is being improperly optimized for drivers. I'm surprised it even works at all or hasn't burned the hardware up ? Uninstall that K7 optimizatrion (Synaptic program manager ?) and get the right update. And that's assuming you got the right version downloading in the first place ?

[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

BTW, it might be quicker and easier to do a clean install, that's if Kernel panics don't allow you the time to get it off your system.

---

### Post by btarlinian on 2006-06-16
[QUOTE=jgcamp99]An Athlon 64 cpu (socket 754 or 939) is not a K7, socket 462 is K7, what you have is the 64 bit AMD K8. Your cpu is being improperly optimized for drivers. I'm surprised it even works at all or hasn't burned the hardware up ? Uninstall that K7 optimizatrion (Synaptic program manager ?) and get the right update. And that's assuming you got the right version downloading in the first place ?

[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

BTW, it might be quicker and easier to do a clean install, that's if Kernel panics don't allow you the time to get it off your system.[/QUOTE]



No, no , no.   there is no k8 optimized 32 bit kernel. If you install 32-bit ubuntu the best you can get is K7, and that shouldn't break your system. That would be like saying istalling linux-386 won't work on a pentium 3 because pentium 3 is a 686.

However, 386 is more likely to work than k7. However, by more likely, I mean 97 % to 96%.
But don't worry about frying your cpu.

---

