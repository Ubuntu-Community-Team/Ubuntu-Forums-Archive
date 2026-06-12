---
title: "Ubuntu using Virtual PC hangs during boot"
date: 2007-08-14
forum: Desktop Environments
---

### Post by TwistedAlliance on 2007-08-14
Hi everyone,
[I]
Before someone starts thinking this is the usual 24 bit to 16 bit graphics problem or the no-mouse issue, it is not. I have already changed the X settings to make it 16 bit by default and my mouse works with the i8042.noloop argument.[/I]

I've been trying to use ubuntu 7.04 on VirtualPC 2007 on my laptop for two days now with no luck. The install completed with no errors with the live CD (after changing the color depth to 16 bits), however after that, 99% of the time ubuntu crashes during boot, not always exactly in the same place but in the vecinity of the "Freeing unused kernel memory" line. Sometimes it gets to "Loading, please wait" and hangs there. None of the keys or combinations work anymore. I said 99% of the time because I've actually made it work 2 times without doing anything special at all, but on the next boot it crashes again. This is a picture of where it hangs when running on recovery mode:

[IMG]http://jonvel9.100webspace.net/Untitled.jpg[/IMG]
[http://jonvel9.100webspace.net/Untitled.jpg](http://jonvel9.100webspace.net/Untitled.jpg)

I cant get the dmesg output coz it hangs before i can get to a command line. I've already tried increasing/decreasing the memory of the VM, disabling the virtual sound card, network card, floppy and cd drive. I've also tried using noapi, nolapi, acpi=off and another bunch of commands i cant remember.

One more thing: when using the live cd to boot, selecting any 16bit resolution and trying recovery mode makes the screen resize and go black with no output at all.  

Any help would be  really appreciated.

My specs:
AMD Athlon 64 X2 Dual core TK53 @1.7 GHz
Quanta 30D3 Motherboard
1GB RAM
Windows Vista Home Premium (32-bit)

---

### Post by TwistedAlliance on 2007-08-15
Nevermind. I switched to VMWare and it works great. :guitar:

---

