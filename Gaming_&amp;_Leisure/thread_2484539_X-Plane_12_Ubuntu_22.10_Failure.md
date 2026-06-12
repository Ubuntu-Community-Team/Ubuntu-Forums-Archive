---
title: "X-Plane 12 Ubuntu 22.10 Failure"
date: 2023-03-02
forum: Gaming &amp; Leisure
---

### Post by lisanels47 on 2023-03-02
I've been running X-Plane 11/12 on ubuntu with no issues at all.  It runs great!
But after switching to ubuntu 22.10 my rudder pedals no longer work, but the yoke does.
I have the Saitek setup.  
Researching it I find the below permissions on the joystick devices.
When plugged in, both js0 and js1 show up just fine as usb devices, and the ubuntu joystick app sees them as well.
Both X-Plane 11 and 12 do not access the rudder pedals.  Even with only the rudder pedels plugged in.
I backed down to ubuntu 22.04 and they now work fine again.

For the Yoke ONLY:
```
lisa@lisa-Legion-Y545-PG0:~$ getfacl /dev/input/js0
getfacl: Removing leading '/' from absolute path names
# file: dev/input/js0
# owner: roo
# group: input
user::rw-
**user:lisa:rw-**
group::rw-
mask::rw-
other::r--
```
For the Pedals ONLY:
```
lisa@lisa-Legion-Y545-PG0:~$ getfacl /dev/input/js0
getfacl: Removing leading '/' from absolute path names
# file: dev/input/js0
# owner: root
# group: input
user::rw-
group::rw-
other::r--
```

---

### Post by DuckHook on 2023-03-02
I strongly recommend staying with only LTS releases like Bionic (22.04).

"If it ain't broke, don't fix it."

Don't upgrade until 24.04 and, even then, only after version 24.04.01 has come out and been stress&#8209;tested by the larger Ubuntu community. In addition to the foregoing, you may want to install X-Plane in a LiveUSB version first to check out if it works before upgrading.

[LIST=1]
[*]Are there other reasons that you must run 22.10?
[*]Have you considered Flightgear? It's a Linux&#8209;friendly project (indeed, started out as exclusively Linux), has a large mod community, is FOSS and is free as in both beer and speech. Not sure if it will have the same Saitek problems on 22.10 though. I only run LTS versions.
[/LIST]

---

### Post by ajgreeny on 2023-03-03
Just to avoid possible confusion, 22.04 is Focal, 20.04 is Bionic.

Apart from that minor error I totally agree with DuckHook; stick with LTS  versions only for your main system.
I try all intermediate versions as virtual systems in KVM/QEMU  but only to see how they're progressing, not for my main use.

---

### Post by DuckHook on 2023-03-03
> **ajgreeny said:**
> Just to avoid possible confusion, 22.04 is Focal, 20.04 is Bionic…
My bad. :sad:

**EDIT**

Waitaminute…

22.04 is *Jammy*.
20.04 is Focal, and 18.04 is Bionic.

Sorry to be the bearer of bad news, ajgreeny, but you are joining my losing&#8209;my&#8209;marbles club. :lolflag:

---

### Post by ajgreeny on 2023-03-04
Oh good grief, so I am!!

That's a result of dual booting focal and jammy and at the time I posted using focal which I haven't for a long time.

Sorry for the total confusion, but delighted it's not only me that goofs up occasionally.
Perhaps I'll stick to numbers rather than code names as it will be safer.

---

