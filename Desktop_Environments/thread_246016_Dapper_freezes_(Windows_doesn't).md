---
title: "Dapper freezes (Windows doesn't)"
date: 2006-08-28
forum: Desktop Environments
---

### Post by jesserosenthal on 2006-08-28
Dear all,

Hope you can help with a strange problem. I have a Fujitsu Lifebook S6210 laptop, which has been happily running linux (debian and Ubuntu) for over two years.

Recently I had a small liquid spill. After drying, everything *seems* to work, except for the ethernet card. I took it in to the shop for a diagnosis, and they said the same thing (though I don't know if they even opened it up, or just played around with it for a bit).

Since the spill, Dapper has been freezing and crashing occasionally. This was to be expected, but the odd thing is that, with the exception of ethernet card, Windows seems to work fine, and hasn't crashed once.

In fact, Ubuntu used to even have problems booting. I solved this by blacklisting the ethernet card's driver (b44) and removing eth0 from /etc/network/interfaces. So I can always boot now. But one of the the following two things will eventually occur:

1. Everything freezes altogether.
2. The mouse starts skipping, often not moving at all. I can switch to a virtual console, but it doesn't do anything after I enter a username. Doesn't freeze (I can ctrl-c) but just doesn't do anything.

So, my question is, how can I find out what is causing this problem on the Ubuntu side? I've run fsck, and looked for bad blocks, and there doesn't seem to be any problem there. I've also run memtest, and it came back okay. None of the logs that I've looked at (syslog, kern.log, messages) seems to tell me much of anything.

I'd be willing to believe that I'd just messed up my hardware beyond repair with the coffee spill. In particular, since the problems seems to happen when I'm down- or uploading (though not only then), I'd think it might be my wireless card. But Windows is in another partition, working like a charm.

So how can I track down what hardware is working under windows but isn't under Dapper?

Thanks for any help,
Jesse

---

### Post by Ocxic on 2006-08-28
since your ethernet card isn't workin properly, i would suggest removing that pice of hardware from your computer and see it ubuntu still crashes.

one piece of faulty hardware, no matter what it is, can still cause problems for your computer.

---

### Post by jesserosenthal on 2006-08-29
I did ask tech folks about that. Unfortunately, since it's a laptop, I've been told that I can't simply remove the card.

---

### Post by KillerBOB on 2006-08-29
Maybe it is possible to disable the nic from Bios settings? I know that is almost always the case atleast with desktop PC's. Haven't played with much laptops though. That way you won't need blacklisting the module and ubuntu might not hang on you.

Good luck

---

### Post by vierranet on 2006-08-29
I have had a simalar issue, this is what I did.

Using gedit from the command line:

"sudo gedit /boot/grub/menu.lst" (without quotes)

Go down to the kernels list, on the kernel line add the following:

noapic
nolapic
pci=noacpi

the kernel line will now look something like:

title Ubuntu, kernel 2.6.12-10-k7
root (hd0,0)
kernel /vmlinuz-2.6.12-10-k7 root=/dev/sda3 ro quiet noapic nolapic pci=noacpi splash
initrd /initrd.img-2.6.12-10-k7
savedefault
boot

Then download BUM (Boot Up Manager) once done goto Services from the Administration menu to disbale the following:

acpid
apmd
powernowd
acpi-support

I have not had any crashs in weeks. Hope this helps.

---

### Post by jesserosenthal on 2006-08-30
Thanks for your suggestions, everyone. Killerbob, I did manage to disable the lan port from the bios. (Disabled the modem for good measure.) Trying it out now. My assumption is that there's some other problem that the tech guys didn't look at, but I'm working with my fingers crossed until then.

Vierranet, I'd prefer to hold on to my power management. But if it continues to crash, that's the next thing I'll try. I did without working acpi on linux, after all. Until I installed Ubuntu, that is.

Thanks all,
Jesse

---

