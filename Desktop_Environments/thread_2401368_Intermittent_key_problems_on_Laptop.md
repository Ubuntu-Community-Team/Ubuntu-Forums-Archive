---
title: "Intermittent key problems on Laptop"
date: 2018-09-17
forum: Desktop Environments
---

### Post by lister171254 on 2018-09-17
Have had my laptop for years and never had any issues with the keys.

A few days ago I noticed that some keys (n, t, b, h, up arrow) stopped working intermittently. Thinking it had something to do with additional software I installed or one of the latest upgrades I did a fresh install of 18.04

I encountered the same issue straight away. A long time ago, there was an easy way to configure which keyboard you use, but no there seem to be a number of different ways of doing this.

My keyboard is defined as US with dead keys; from memory this was always an issue on Australian keyboards.

Appreciate any hints on how I can resolve this issues.

Thanks

---

### Post by lister171254 on 2018-09-17
Had another look and the layout for the US International keyboard with dead keys is wrong. it looks like a german keyboard (see attached)

---

### Post by Autodave on 2018-09-17
Sounds to me like you have a sticking key.  Try going into a text typing program and try each of those keys many times. Quickly.  If a key suddenly starts to work, you know that that is the bad one.  It could also be another key that is stuck and preventing those keys to work.  Try every key repeatedly, even if they don't really type anything (Shift, Del, etc.) You may gte lucky and find out which one is sticking.

---

### Post by Holger_Gehrke on 2018-09-17
> **lister171254 said:**
> Had another look and the layout for the US International keyboard with dead keys is wrong. it looks like a german keyboard (see attached)

I'm sitting at a German keyboard right now and that looks nothing like that ;)

One has to know how to read these keyboard maps. Every key has four characters associated with it, the base (bottom left), the key with shift (top left), the key with AltGr (bottom right) and with both Shift and AltGr (top right). This is indeed an American layout; "y" and "z" would be switched around on a German keyboard and the Umlauts would be on the far left where the "[", ";" and "¨" are; there are a lot of other differences, but these are the most obvious.

Holger

---

### Post by lister171254 on 2018-09-18
Have changed the keyboard as per this post [https://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu](https://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu)
It now looks like the attached and have not had any issues so far.

---

### Post by Autodave on 2018-09-18
Good job!  Glad you got it figured out.  Please remember to mark this post as *Solved *by going to the top (your first post) and click on Thread Tools and then Mark as Solved.

---

### Post by lister171254 on 2018-09-19
Marked this in the morning as solved, but the problem just happened again.

I'm sure i's not a hardware issue (i.e. keys really stick) as when this happens none of the specified keys work. It just looks like the input is ignored for a while on certain keys (n,t,b,h, up arrow); it actually happened while I typed this message

There is one thing I noticed, though.

While I typed this message I did a big copy job in a terminal widow via the rsync command. The window that runs the rsync is minimized and after a while I'm getting the issue where the above keys don't work. I just tried it and when I stop the rsync or open the minimized window everything works ok again.

Doesn't make any sense to me, but maybe someone else

Thanks

---

### Post by Autodave on 2018-09-19
I can't see where any program running would only affect certain keys.  Try finding an external keyboard and trying that in the same scenario. If it works, then you know where the problem is.

---

### Post by lister171254 on 2018-09-30
I think it's some sort of resource issue, but why it would only affect the few keys I identified I don't know

[LIST=1]
[*]Did a copy of my (large) music collection (flac format) between 2 external usb disks. Thought I found the problem as during the copying, the 4 keys (but none of the others) stopped working. When I stopped the copy, all keys worked again.  Thought that I found the problem, but when I deleted the music collection from on disk and repeated the copy, keys worked ok (all the time) until the copy finished
[*]Ran a VM and put the Laptop into Standby by closing the Laptop lid. When I opened the lid and the system came back up, the 4 keys stopped working again; the HD light was on pretty much permanently after the start, which I think was related to the VM. I plugged in an external keyboard and all keys worked ok on that. After killing the VM, all keys worked ok on my laptop
[/LIST]

---

### Post by Autodave on 2018-09-30
You have a sticking key......happens a lot especially on laptops.

---

