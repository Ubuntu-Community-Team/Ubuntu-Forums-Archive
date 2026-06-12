---
title: "Wheel moue lost synchronization"
date: 2006-08-23
forum: Desktop Environments
---

### Post by mauro007 on 2006-08-23
I'm having a problem with my Xubuntu box and I don't know where to turn:
I keep my box on all the time, and every 2-3 days my mouse goes crazy and doens't respond and I need to reboot my pc.
Yesterday I run memtest86 for 12 hours and it didn't find any errors, this evening after coming back from work, I moved my mouse and the cursor started behaving very erratically, I decided to switch to tty1 since xfce would't respond anymore, I checked syslog and I copied and pasted some lines:

Aug 23 16:17:01 Nippur /USR/SBIN/CRON[8825]: (root) CMD (   run-parts --report /etc/cron.hourly)
Aug 23 16:36:37 Nippur -- MARK --
Aug 23 16:56:38 Nippur -- MARK --
Aug 23 17:16:38 Nippur -- MARK --
Aug 23 17:17:01 Nippur /USR/SBIN/CRON[8905]: (root) CMD (   run-parts --report /etc/cron.hourly)
Aug 23 17:27:32 Nippur dhclient: DHCPREQUEST on eth0 to 192.168.1.254 port 67
Aug 23 17:27:32 Nippur dhclient: DHCPACK from 192.168.1.254
Aug 23 17:27:33 Nippur dhclient: bound to 192.168.1.102 -- renewal in 39866 seconds.

"here starts the problem":

Aug 23 17:39:46 Nippur kernel: [17261297.476000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Aug 23 17:39:47 Nippur kernel: [17261298.768000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Aug 23 17:39:48 Nippur kernel: [17261299.772000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Aug 23 17:39:55 Nippur kernel: [17261306.652000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Aug 23 17:40:45 Nippur kernel: [17261356.796000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Aug 23 17:41:36 Nippur kernel: [17261408.008000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Aug 23 17:51:57 Nippur kernel: [17262029.088000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Aug 23 17:54:44 Nippur kernel: [17262196.128000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Aug 23 18:12:55 Nippur kernel: [17263287.160000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Aug 23 18:15:13 Nippur kernel: [17263424.528000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Aug 23 18:17:01 Nippur /USR/SBIN/CRON[8986]: (root) CMD (   run-parts --report /etc/cron.hourly)
Aug 23 18:19:17 Nippur kernel: [17263668.664000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Aug 23 18:19:27 Nippur kernel: [17263677.660000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Aug 23 18:19:28 Nippur kernel: [17263680.124000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.

(I deleted some lines for space purpose)

I than decided I had enough and from tty1 I restarted the pc: 

Aug 23 18:19:59 Nippur init: Switching to runlevel: 6
Aug 23 18:20:16 Nippur kernel: Kernel logging (proc) stopped.
Aug 23 18:20:16 Nippur kernel: Kernel log daemon terminating.
Aug 23 18:20:16 Nippur exiting on signal 15
Aug 23 18:21:38 Nippur syslogd 1.4.1#17ubuntu7: restart.
Aug 23 18:21:38 Nippur kernel: Inspecting /boot/System.map-2.6.15-26-386
Aug 23 18:21:39 Nippur kernel: Loaded 23037 symbols from /boot/System.map-2.6.15-26-386.
Aug 23 18:21:39 Nippur kernel: Symbols match kernel version 2.6.15.
Aug 23 18:21:39 Nippur kernel: No module symbols loaded - kernel modules not enabled.
Aug 23 18:21:39 Nippur kernel: [17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
 
...and rebooted the pc.

I am running a Celeron 650 Mhz with 512 mb ram and a Nvidia 3d Card (don't remember the model)
The pc is also connected via a kvm switch with another pc: a windwos 2000 box, both on a dsl router. mouse and keyboard are ps/2

Two days ago similar thing happened: after moving my mouse for a while the system restarted by itself, after all applications kept switching between background and foreground.

One more thing: I use streamtuner all the time for listening music and I usually have 2-3 teminal opened and maybe 4-5 firefox session open.

I've been having problems since day one, there isn't a propper xubuntu forum, hence I am posting this problem here.
This is driving me mad. Please help.
Thanks

---

### Post by auburn on 2006-09-11
me too. my mouse is having epileptic fits. I changed the optical mouse to a ball-mouse. No change. 
```
$ dmesg|tail
[17236690.052000] psmouse.c: 
bad data from KBC - bad parity
[17236696.576000] psmouse.c:
 Wheel Mouse at isa0060/serio1/input0 
lost synchronization, throwing 
3 bytes away.
```
I'm using a kvm (also), fully updated dapper ubuntu and my xorg.conf identifies my mouse as:
```

Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
  Option      "Device"    "/dev/input/mice"
  Option      "Protocol"  "ExplorerPS/2"
  Option      "ZAxisMapping"     "4 5"
  Option      "Emulate3Buttons"  "true"
EndSection

```
I have an amd cpu and an nvidia geforce fx5200 video card.
Here is a thread covering a similar issue:
[http://forums.gentoo.org/viewtopic-t-66958-postdays-0-postorder-asc-start-0.html?sid=2de788d469902e7f43adab71405e1aea](http://forums.gentoo.org/viewtopic-t-66958-postdays-0-postorder-asc-start-0.html?sid=2de788d469902e7f43adab71405e1aea)

---

