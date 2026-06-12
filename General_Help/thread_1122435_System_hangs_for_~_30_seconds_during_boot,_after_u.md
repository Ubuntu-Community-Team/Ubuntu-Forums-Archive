---
title: "System hangs for ~ 30 seconds during boot, after usplash finishes"
date: 2009-04-11
forum: General Help
---

### Post by dt_ on 2009-04-11
Hi everyone,

I'm running Ubuntu 9.04 Jaunty beta (though I did have this problem with 8.10 also) on a Dell XPS M1530 laptop, and I have a strange issue where the boot process stalls on occasion (but NOT ALWAYS), after the Ubuntu splash screen finishes loading.

Normally, the system boots up, the usplash finishes, then there's a black screen for a few seconds, the mouse cursor shows up, and the GDM comes up. But from time to time, I'd say every third boot or so, I have a strange issue that where after the usplash is done, the screen turns black and just sits there for about 30 seconds without doing anything. This is followed by the screen turning on and off once or twice, and then a bunch of text that goes something like this..

```
* Starting network connection manager NetworkManager
* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon
* Starting Common Unix Printing System: cupsd
* PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned

```

and so on and so forth until the last two lines..

```
/dev/sda:
 setting Advanced Power Management level to 0x80 (128)

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
```

It shows this text for about two seconds, and then proceeds normally to the GDM.

The only abnormality I see here is that the asterisk "*" next to the "PulseAudio configured for..." line is orange instead of the usual gray. Does this mean there's a problem there? And if so, is that necessarily the source of my boot-up stall?

Any help would be much appreciated! :)

thanks,
dt_

---

### Post by DeMus on 2009-04-11
> **dt_ said:**
> Hi everyone,

I'm running Ubuntu 9.04 Jaunty beta (though I did have this problem with 8.10 also) on a Dell XPS M1530 laptop, and I have a strange issue where the boot process stalls on occasion (but NOT ALWAYS), after the Ubuntu splash screen finishes loading.

Normally, the system boots up, the usplash finishes, then there's a black screen for a few seconds, the mouse cursor shows up, and the GDM comes up. But from time to time, I'd say every third boot or so, I have a strange issue that where after the usplash is done, the screen turns black and just sits there for about 30 seconds without doing anything. This is followed by the screen turning on and off once or twice, and then a bunch of text that goes something like this..

```
* Starting network connection manager NetworkManager
* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon
* Starting Common Unix Printing System: cupsd
* PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned

```

and so on and so forth until the last two lines..

```
/dev/sda:
 setting Advanced Power Management level to 0x80 (128)

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
```

It shows this text for about two seconds, and then proceeds normally to the GDM.

The only abnormality I see here is that the asterisk "*" next to the "PulseAudio configured for..." line is orange instead of the usual gray. Does this mean there's a problem there? And if so, is that necessarily the source of my boot-up stall?

Any help would be much appreciated! :)

thanks,
dt_

Hi,
I just looked in the /etc/default folder but there is no saned here, so it must be something typical for your computer.
The message says edit saned. Have you looked into that to see what it is?
```
* Starting network connection manager NetworkManager
* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon
* Starting Common Unix Printing System: cupsd
* PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned

```

Maybe that can give you an idea of what is wrong.

---

### Post by dt_ on 2009-04-14
Thanks for your reply :)
It turns out I do have a 'saned' file in /etc/default/, however, when I change this line:

```
# Set to yes to start saned
RUN=no
``` 

to say "RUN=yes" ,   it seems that the system hangs for even *longer* than it would with RUN=no ! Or at least, for the same amount. So I don't think this is the problem.

I do notice that sometimes when I boot up the machine and log in, my wireless driver doesn't seem to be working and I have to deactivate and reactivate my Broadcom wireless driver from System -> Administration -> Hardware Drivers before I can connect to a wireless network.  Could this maybe be related to my 'system hangs' problem?

Thanks!

**Edit:** OK, I doubt the wireless driver is the problem because I deactivated the Broadcom driver and rebooted, only to find the same 'hang' behavior. I'm going to check the NVIDIA driver next (180).

---

### Post by dt_ on 2009-04-14
Alright I'm pretty sure the problem has to do with the NVIDIA drivers, as others seem to have had a similar issue..   [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/333048](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/333048)

And upon deactivating these drivers I rebooted twice -- and both times there was no 'hang'.

---

