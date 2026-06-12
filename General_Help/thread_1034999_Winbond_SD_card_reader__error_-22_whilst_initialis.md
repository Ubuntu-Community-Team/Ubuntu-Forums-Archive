---
title: "Winbond SD card reader : error -22 whilst initialising SDIO card"
date: 2009-01-09
forum: General Help
---

### Post by heindsight on 2009-01-09
I've been having some strange problems with my SD card reader on my laptop running Hardy.

Approximately 85% of the time, when I insert an SD card, nothing happens. Or at least almost nothing - I do get an error in the logs saying:
mmc0: error -22 whilst initialising SDIO card
but if i remove and reinsert the card enough times, eventually the card is read and mounted properly.

I never had any such problems with previous versions of ubuntu, but it's been quite a while since i tried to use an SD card in this machine so I can't be certain whether it's a problem with my card reader or if it's a bug in the wbsd or mmc_core modules.

I'm posting relevant excerpts from /var/log/syslog:

```
Jan  9 14:42:51 getafix kernel: [   23.862100] wbsd: Winbond W83L51xD SD/MMC card interface driver
Jan  9 14:42:51 getafix kernel: [   23.862103] wbsd: Copyright(c) Pierre Ossman
Jan  9 14:42:51 getafix kernel: [   23.862686] wbsd 00:0a: activated
Jan  9 14:42:51 getafix kernel: [   23.867760] mmc0: W83L51xD id 7112 at 0x210 irq 10 FIFO PnP
...
...
Jan  9 14:44:15 getafix kernel: [  201.977828] mmc0: error -22 whilst initialising SDIO card
Jan  9 14:44:19 getafix kernel: [  205.766489] mmc0: error -22 whilst initialising SDIO card
Jan  9 14:44:22 getafix kernel: [  208.645295] mmc0: error -22 whilst initialising SDIO card
Jan  9 14:44:26 getafix kernel: [  212.429687] mmc0: error -22 whilst initialising SDIO card
Jan  9 14:44:29 getafix kernel: [  215.392823] mmc0: error -22 whilst initialising SDIO card
Jan  9 14:44:31 getafix kernel: [  218.237605] mmc0: error -22 whilst initialising SDIO card
Jan  9 14:44:36 getafix kernel: [  222.357314] mmc0: error -22 whilst initialising SDIO card
Jan  9 14:44:45 getafix kernel: [  231.659989] mmc0: error -22 whilst initialising SDIO card
Jan  9 14:44:49 getafix kernel: [  235.999947] mmc0: new SD card at address 2333
Jan  9 14:44:49 getafix kernel: [  236.070205] isa bounce pool size: 16 pages
Jan  9 14:44:49 getafix kernel: [  236.072027] mmcblk0: mmc0:2333 S016B 14560KiB 
Jan  9 14:44:49 getafix kernel: [  236.072405]  mmcblk0: p1
Jan  9 14:44:51 getafix hald: mounted /dev/mmcblk0p1 on behalf of uid 1000

```

I've been doing some googling, but I can't figure out what this error -22 means. Anyone got a clue how to get to the bottom of this?

---

### Post by heindsight on 2009-01-11
I might add that the problem is definitely not with the SD card. I've tried a few different cards and all of them work perfectly in other computers and in my camera.

---

### Post by heindsight on 2009-01-14
Well, last night I built and booted a kernel with CONFIG_MMC_DEBUG enabled (that was the only change I made from the current Hardy kernel 2.6.24-23-generic). I'm hoping the debug output I got in the logs from that will help me get to the bottom of this little problem I'm having. I'll probably have to spend quite a lot of time sifting through the logs and the source in drivers/mmc before I can figure out what's happening.

In the mean time, I'm attaching relevant extracts from syslog with CONFIG_MMC_DEBUG enabled here, in case someone else is bored and feels like taking a stab at it. ;)

---

### Post by heindsight on 2009-02-23
I gave up on this. I spent ages sifting through the source and the logs and I still have no idea what the cause of the problem is. I can only assume that my card reader is on the blink (it is a four year old machine, I guess some hardware failure is inevitable)

---

### Post by torp74 on 2009-02-23
> **heindsight said:**
> I gave up on this. I spent ages sifting through the source and the logs and I still have no idea what the cause of the problem is. I can only assume that my card reader is on the blink (it is a four year old machine, I guess some hardware failure is inevitable)

One could always use a card reader inserted into a USB slot.

torp74

---

### Post by heindsight on 2009-02-23
> **torp74 said:**
> One could always use a card reader inserted into a USB slot.

torp74

True, except I don't have any free USB slots so I'd have to buy a USB hub too. I think I might just buy myself a new laptop.

---

### Post by grolain on 2009-03-29
Hello, I have exactly the same problem on my laptop Compal CL51.

I have also to introduce the card several times before it is recognized. And when it does not work, I have similar error message in dmesg : mmc0: error -22 whilst initialising SDIO card

It is not a matter of SD card issue (same behaviour with all SD cards).

It worked perfectly on this laptop with windows xp and with ubuntu 7.10.
It does not work with ubuntu 8.04, and found no improvement with 8.10.

So I suspect that a change in new kernels, mixed with my hardware, provoke this trouble.

Could you solve this yourself ?

---

### Post by heindsight on 2009-03-29
> **grolain said:**
> Hello, I have exactly the same problem on my laptop Compal CL51.

I have also to introduce the card several times before it is recognized. And when it does not work, I have similar error message in dmesg : mmc0: error -22 whilst initialising SDIO card

It is not a matter of SD card issue (same behaviour with all SD cards).

It worked perfectly on this laptop with windows xp and with ubuntu 7.10.
It does not work with ubuntu 8.04, and found no improvement with 8.10.

So I suspect that a change in new kernels, mixed with my hardware, provoke this trouble.

Could you solve this yourself ?

Interesting, I also have a Compal CL51. I thought perhaps my problems were due to hardware failure (after all, the machine is 4 years old), but if you have the same problem on the same hardware then there may be more to it.

---

### Post by grolain on 2009-03-30
Yes, very interesting. Well, definitely it is not a hardware failure : I just tried with an "old" ubuntu 7.10 this week-end, it still works.
By the way, could you upgrade the BIOS of your compal ? I tried several ways with last version 2.10, even under windows, none works. I thought a BIOS upgrade could solve this SD issue.
I don't know what to do .....

---

### Post by heindsight on 2009-03-31
> **grolain said:**
> Yes, very interesting. Well, definitely it is not a hardware failure : I just tried with an "old" ubuntu 7.10 this week-end, it still works.


I've been wanting to try that, but I haven't been able to get hold of an old CD. If it works on 7.10 but not 8.04 or 8.10 then it's probably a bug in the wbsd kernel module. I'll see if I can get hold of the kernel sources for 7.10 and see if I can figure out what's changed.

> **grolain said:**
> 
By the way, could you upgrade the BIOS of your compal ? I tried several ways with last version 2.10, even under windows, none works. I thought a BIOS upgrade could solve this SD issue.
I don't know what to do .....

I did manage to update the BIOS once, a few years ago, using a [FreeDOS]("http://www.freedos.org/") boot image (I've never had Windows installed on this machine). I think I have a copy of the 2.10 BIOS update lying around somewhere, but I haven't tried to upgrade it. I doubt if a BIOS update would fix the card reader problem anyway.

---

