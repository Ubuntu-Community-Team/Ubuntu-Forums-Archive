---
title: "[SOLVED] Multiseat bootup problem"
date: 2008-11-18
forum: Desktop Environments
---

### Post by phenym on 2008-11-18
I have multiseat X (3 seats) working sort-of nicely on a small server using three graphics cards.

I am running 8.10 AMD64.

I have played with the config a lot and have the Input devices configured via "Dev Phys" and have turned off the feature that allows X to dynamically alter the input devices (my understanding of it...  *Option "DisableModInDev" "true"* under "Serverflags"). I'm also using the IsolateDevice option for PCI.

My problem is on bootup... the system comes up and the only seat that is active is the main seat (seat 0). I have to log into that seat, go to seat 1 and unplug the keyboard and mouse (in turn, both at once doesn't work) and seat 1 starts to work. Same for seat 2.

Is there any way to get all three seats ready for login from bootup without having to play with unplugging/re-plugging the usb input devices?

I use gdm and currently have (X0, X1 and X2 are symlinks to X):

```

[servers]
0=Standard0
1=Standard1
2=Standard2

[server-Standard0]
name=Standard server
command=/usr/X11R6/bin/X0 -nolisten tcp -novtswitch -sharevts -layout seat0
flexible=true

[server-Standard1]
name=Standard server
command=/usr/X11R6/bin/X1 -nolisten tcp -novtswitch -sharevts -layout seat1
flexible=true

[server-Standard2]
name=Standard server
command=/usr/X11R6/bin/X2 -nolisten tcp -novtswitch -sharevts -layout seat2
flexible=true
```

I've thought of doing the following, but haven't tried it yet:

```
[servers]
0=Standard0
1=Standard1
2=Standard2

[server-Standard0]
name=Standard server
command=/usr/X11R6/bin/X0 -nolisten tcp -novtswitch -sharevts -layout seat0
flexible=true

[server-Standard1]
name=Standard server
command=sleep 60; /usr/X11R6/bin/X1 -nolisten tcp -novtswitch -sharevts -layout seat1
flexible=true

[server-Standard2]
name=Standard server
command=sleep 120; /usr/X11R6/bin/X2 -nolisten tcp -novtswitch -sharevts -layout seat2
flexible=true
```

Would that work to bring the servers up one at a time and maybe get the input devices responding properly?

If the power goes out (we do have a UPS) and the system is forced to shutdown, I would like my team to be able to just hit the power button and be up and running. Otherwise I have to write a mini-manual just to get the thing to bootup properly.

BTW... Performance is fantastic on all three seats using MSI nvidia-based cards. :)

---

### Post by phenym on 2008-12-10
Still having this problem as of 12/10/2008. I have noticed that there have been a number of kernel oopses getting recorded in the syslog and the system becomes unstable after a while. I have now tried turning APIC off.

Booting this thing is a pain and having to reboot often is becoming a chore.

Phenym

---

### Post by phenym on 2008-12-12
Figured it out... I had to add:

```

Section "ServerFlags"
    Option "DisableModInDev" "true"
    Option "AutoAddDevices" "off"
EndSection

```

To my xorg.conf file.

Now each head comes up with the appropriate input device.

-phenym

---

### Post by mar17 on 2009-02-15
Hi,

I am very interested in doing the same thing with two computers. Running ubuntu 8.10 64 bits as well. :) I am kind of new to ubuntu... Could you post your xorg.conf file as well to get some guidance?

Thanks!
mar17

---

### Post by second.exodous on 2009-03-06
I was just wondering how this was going.  What are the capabilities of your system?  You said you had 3 video cards, is each seat able to play games?

I've started to do research on this but can't find any information on the game side of multi-seat systems.

---

### Post by brucewestfall on 2009-03-30
I am in the same situation.  Ubunut 8.10 64.  I have 2 video cards, although what I use right now is an Nvidia card with 2 heads.  I can get the big superwide screen, but in my trials I broke things a few times.

I am certainly one to experiment, but if the first poster could give some more details or links that were used, I am sure more than just 2 people would benefit.

It would be great to have 2 separate sessions running concurrently.

I am still searching...

---

