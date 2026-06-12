---
title: "Ubuntu 12.04 won't shut down,reboot automatically afetr shut down"
date: 2012-06-30
forum: Desktop Environments
---

### Post by nltzou on 2012-06-30
Hi,

I'm using Ubuntu 12.04.
The computer automatically reboot after shut down.

CPU:
intel i7 3770k

Graphic cards:
nvidia quadro nvs295
nvidia quadro 2000

Mother board:
DZ77GA-70K

It seems like some other users have similar problem.

I tried changing the grub file.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
And I don't have [FONT=monospace]module [/FONT]ehci_hcd
I tried using the command line to shut down.
The computer just won't shut down.

Can any one give me some suggestion??

Thank you all in advance!!

Nicholas

---

### Post by Ubun2to on 2012-06-30
Try shutting down via terminal.
```
sudo shutdown -p now
```
If you want to reboot from terminal:
```
sudo shutdown -r now
```
Also, this should be in the General forum. Desktop Environments have nothing to do with shutting down.

---

### Post by MooseDog on 2012-07-01
> **nltzou said:**
> Hi,

I'm using Ubuntu 12.04.
The computer automatically reboot after shut down.

...

It seems like some other users have similar problem.

I tried changing the grub file.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
And I don't have [FONT=monospace]module [/FONT]ehci_hcd
I tried using the command line to shut down.
The computer just won't shut down.


this.

Googled the problem ad nauseum, no solution.

btw, it's

```
sudo shutdown -h now
```

and even that does not work properly, as 12.04 64bit still automatically reboots :(.

Any hints from this community, it's consistently been awesome!

thx!

---

### Post by era506 on 2012-08-04
> **nltzou said:**
> Hi,

I'm using Ubuntu 12.04.
The computer automatically reboot after shut down.

CPU:
intel i7 3770k

Graphic cards:
nvidia quadro nvs295
nvidia quadro 2000

Mother board:
DZ77GA-70K

It seems like some other users have similar problem.

I tried changing the grub file.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
And I don't have [FONT=monospace]module [/FONT]ehci_hcd
I tried using the command line to shut down.
The computer just won't shut down.

Can any one give me some suggestion??

Thank you all in advance!!

Nicholas

This is driving me crazy! I have the same processor and motherboard and I just can't get it to shutdown, no solution has worked so far :(

Suggestions anyone?

P.D. sudo shutdown -h now still reboots :@

EDIT: Worth mentioning, I dual boot with Windows 7 and it shuts down properly...

---

### Post by dcsoldschool53 on 2012-08-04
If you do the command```
man shutdown
```in a terminal, it will tell you that the code is actually```
sudo shutdown -P now
```btw. It will power off the system after it is brought down.

---

### Post by era506 on 2012-08-04
> **dcsoldschool53 said:**
> If you ```
man shutdown
``` the code is actually```
sudo shutdown -P now
```btw. It will power off the system after it is brought down.

Nope, I've tried that one too and still reboots... I just installed Kernel 3.4 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/) and will reboot in a bit to try ;) It supposedly fixes some issues with Intel's new Ivybridge products so... let's give it a try :D

EDIT: kernel 3.4 didn't work :( :sigh:

---

### Post by dcsoldschool53 on 2012-08-04
If that does not work, try shutting down your modem and router first, then: run the```
sudo shutdown -P now
``` command.

---

### Post by era506 on 2012-08-04
Interesting! I disabled Wake on LAN from my BIOS settings and it now properly shuts down O.o 
How is this only happening with Ubuntu and not with Windows? It seems to me that it is OS related since Windows always shuts down properly. How can I configure Ubuntu for this without disabling the option in my BIOS?

---

### Post by dcsoldschool53 on 2012-08-04
There is a program still running that won't let you shutdown. I'm guessing it is either your internet connection or your network itself.Sorry just saw your last post.

---

### Post by era506 on 2012-08-04
Interesting... I'm still wondering why it doesn't happen with Windows... I currently have my router directly plugged in to my PC's ethernet port so I'm guessing if I connect through WiFi it will shut down (I'll try this later as I can't reboot right now)
In the meantime I'll try tinkering with my router's settings (I have a Linksys X2000)

---

### Post by dcsoldschool53 on 2012-08-04
I just found these to sites in ubuntu help [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan) and [https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html) maybe they can help you. It's a start.

---

### Post by era506 on 2012-08-04
> **dcsoldschool53 said:**
> I just found these to sites in ubuntu help [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan) and [https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html) maybe they can help you. It's a start.

Thanks! I'm currently in no need to have WoL so I'll research later on this. For the time being turning off WoL on my BIOS fixes the shutdown issue.

Again, for future reference, my specs are:

Custom build PC with Ubuntu 12.04 64bits
Intel Core i7 3770K (Ivy Bridge)
Intel Desktop Board DZ77GA-70K

---

