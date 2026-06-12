---
title: "ubuntu 'pausing' constantly"
date: 2006-08-30
forum: Desktop Environments
---

### Post by alewis12345 on 2006-08-30
I installed 6.06 on a spare machine I've had lying around, and although the text installer went fairly smoothly, I've been having issues while running ubuntu.  Every 30 seconds or so, the system will simply 'pause'.  The mouse freezes, and I'm unable to do anything.  After 5-10 seconds I'll get control back and thigns will seem to work normally.  This also happens even if I'm not actively using the system (e.g., you can tell by the screensaver that it's happening even when the SS is activated).

Ideas?

Machine Specs (somewhat rough - built this thing ages ago!):
Intel P4 3.00Ghz
Abit VT7 Mb
1 Gig RAM
WD 120Gig SATA HD

---

### Post by taurus on 2006-08-30
Maybe there is a problem with your graphic card!  What is it and have you installed a driver for it?

---

### Post by Shay Stephens on 2006-08-30
I had a laptop that paused like this, though it was shorter in duration.  The problem wound up being powernowd.  Once I disabled it, the pausing stopped.

You can test it by using this command:

```
sudo /etc/init.d/powernowd stop
```

If that works, you can disable it permanently by installing sysv-rc-conf 
```
apt-get update
sudo apt-get install sysv-rc-conf
```

To run it, just use:
```
sudo sysv-rc-conf
```

And uncheck powernowd

---

### Post by alewis12345 on 2006-08-30
Thanks for the idea - I'll try this tonight and hopefully be back in business.  When you had this issue, was another symptom that the mouse would move erratically and/or disappear?  Sometimes it seems like the mouse can only move in straight (horizontal) lines for several seconds at a time, during which it's partially or totally invisible.

---

### Post by Shay Stephens on 2006-08-30
My symptoms were limited to the mouse freezing for a moment, then moving again.  This repeated at regular intervals.  Once powernowd was turned off, the mouse started working fine.

So you may be having a different problem.  But might be worth trying anyway.

Have you tried a different mouse? Is it an optical mouse?

---

### Post by Andrew1234 on 2006-08-30
I am having the same problem, the mouse freezes but the key board is working fine, this seems to be happening since the xserver update in the last couple of weeks. As before I had no problems and my system was working fine? Any ideas!

---

### Post by xtknight on 2006-08-30
I have this problem when my VM (virtual memory) is maxed out.  Another thing that caused this issue was 'gnash' (open source flash plugin).  There were 200 zombies of it in my process list.

In the terminal, type: **top**
See if you have lots of zombies.  If so, type **ps ax** to find out what the zombies are.

To kill a zombie kill its parent process.  Generally this is Mozilla or one of its variants in the case of gnash.  **sudo killall firefox; sudo killall mozilla; sudo killall epiphany**.  I had to uninstall gnash to keep this from happening.  It was my only choice.  **sudo apt-get remove gnash**

Also type **free** to check out VM usage.  If you recently compiled a new kernel, an option you selected in the config might have affected it too.

For the mouse problems, check **dmesg** to see if a USB hub is getting virtually unplugged.  This can happen if your mouse is defective (but don't assume that unless you see such hotplug messages in dmesg).  Soon after it happens try typing **uptime**.  If your uptime load average is higher than usual (like >4.00) maybe you're having similar process flood problems like gnash.

As mentioned above, AMD Cool'n'Quiet/Powernow/Intel EIST and similar things can also cause this.  My mouse froze up in Windows when I was using an ASUS Motherboard with the AI NOS feature (clock frequency change).

If **all else** fails, see if disabling ACPI and local APIC helps.  (boot kernel with acpi=off nolapic noapic).  Or, disable it in your BIOS.  The BIOS method has worked best for me.

---

### Post by xtknight on 2006-08-30
I noticed a lot of threads on this and now I'm getting the same problem (my PS/2 keyboard and USB mouse are freezing).  I have 85MB of free physical memory so that's not an issue.  No zombies this time.  No gnash.  But I do have a high uptime load average.  And when I unplug/replug in my USB mouse my whole system seems to unfreeze (keyboard and mouse get frozen).  I think it's one of the recent updates.

---

### Post by Andrew1234 on 2006-08-31
Like wise, if you look at the threads there are several now only in the last few days re system and mouse freezing, could this be another bug in the xserver update on Monday, August 21st, as before this update I had no problems, and it does seem to be a GUI issue?

Edit ;- 1/9/2006
If it helps - If I unplug my mouse and plug it in again this seems to work fine, just saves having to restart the PC, but it seems to be getting worse, as it froze as soon as I booted up this morning!!!!!!

---

### Post by Violaine on 2006-09-03
> **Shay Stephens said:**
> I had a laptop that paused like this, though it was shorter in duration.  The problem wound up being powernowd.  Once I disabled it, the pausing stopped.

You can test it by using this command:

```
sudo /etc/init.d/powernowd stop
```

If that works, you can disable it permanently by installing sysv-rc-conf 
```
apt-get update
sudo apt-get install sysv-rc-conf
```

To run it, just use:
```
sudo sysv-rc-conf
```

And uncheck powernowd

Thanks, that did the trick for my Inspiron 8100.  It was hanging for about a second every time it entered the low power state.  Now I just need to try an alternative to powernowd.

---

### Post by Andrew1234 on 2006-09-05
I've tried sudo /etc/init.d/powernowd stop but this makes no difference, 

I am using a Nvida graphics card, after the xserver upgrade I didnot need to reinstall my nvida drivers, could this be an issue! ( If so I have forgot how I installed the drivers can anyone tell me how to reinstall the drivers?)

this is driving me mad, and my mouse socket is getting a little hot with friction!!

---

### Post by Andrew1234 on 2006-09-22
I have uninstalled Skype and Gnucash two days ago, and since  then I have found that my mouse hasn't frozen once. I haven't reinstall them.

Edit 30/9 I had several days without problems but still having the same problem.

---

### Post by JohnnyVW on 2006-09-24
> **Shay Stephens said:**
> I had a laptop that paused like this, though it was shorter in duration.  The problem wound up being powernowd.  Once I disabled it, the pausing stopped.

You can test it by using this command:

```
sudo /etc/init.d/powernowd stop
```

If that works, you can disable it permanently by installing sysv-rc-conf 
```
apt-get update
sudo apt-get install sysv-rc-conf
```

To run it, just use:
```
sudo sysv-rc-conf
```

And uncheck powernowd

I was having the same problem with my Dell Latitude CPX-J.  Disabling powernowd fixed it.  :D

---

### Post by Andrew1234 on 2006-09-30
Has anyone had any sucess on this problem, it does seem to be a bit of a problem as there seem to be more and more threads about it, can any one give me any other ideas to try to crack the problem?

My $dmesg:-
> [17186153.476000] psmouse.c: bad data from KBC - timeout
[17186153.996000] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
[17186165.068000] psmouse.c: bad data from KBC - timeout bad parity
[17186167.088000] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[17186194.672000] psmouse.c: bad data from KBC - timeout
[17186195.476000] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.


I pc is hardly useable at the moment:(

Update :- Change mouse to Optical mouse and its works great now:) :)

---

