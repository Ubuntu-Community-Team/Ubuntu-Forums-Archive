---
title: "Ubuntu 8.10 slower than Vista - Need Help..."
date: 2009-03-18
forum: General Help
---

### Post by ubuwatson on 2009-03-18
I installed Ubuntu 8.10 on my laptop (HP 6775US). I have run previous versions of Ubuntu and they have been fine, stable, and superior in speed.  However 8.10 (clean installation), runs a bit slow and I have not been able to find a solution.

Opening applications seems slow, there is often a delay when opening a file (like a picture) and the overall feeling is that the OS 'seems' sluggish.  Yet everything works as expected: network, disk, and graphics performance seem perfect (network bandwidth is tops, disk read/writes seem fine, and compiz effects are fluid and smooth).  I have no issues or problems otherwise, all of my hardware was detected at installation and the OS works as expected.  My problem is is that even Vista SP1 runs more smoothly than Ubuntu 8.10, I can't figure that out for the life of me - it just doesn't make any sense.

I would much rather run Ubuntu, but I might have to switch back....Save Me !

Does anyone have any thoughts, ideas, or suggestions ?

---

### Post by Scar-face on 2009-03-18
are you running on battery power?
I find my ubuntu to be quite slow when I run on battery power.
When I'm on AC I have no problems..

---

### Post by lykwydchykyn on 2009-03-18
Do you know what your graphics chip is?  Often slowness is a result of loading a generic video driver.

If you don't know, post the output of 'lspci'

---

### Post by ubuwatson on 2009-03-18
My notebook is plugged in 90% of the time.

The card is an Nvidia 8400 (256 M).  Ubuntu detected the card and loaded the Nvidia drivers for it, and compiz effects are fast, fluid, and smooth, yet overall operation of the OS seems sluggish.


This is a rather fast machine and overall performance under Vista is great, I just prefer Ubuntu as I believe it is a better OS and I would like to support the community by developing applications for it.

---

### Post by lykwydchykyn on 2009-03-18
You may have to be more specific about what sorts of things are slow.  I assume you've watched the output of "top" while working, to see if anything's eating up resources?  Are you sure the processor is running at full speed?

Without some concrete data it's hard to know what to suggest.

---

### Post by phr0ze on 2009-03-18
It seems to me you are saying file operations, or better, nautilis performance is slow. I notice if I double click a picture in nautilis I have a bit of a delay too as the default viewer spins up.

Load xfce desktop for fun and see how that performs.

---

### Post by lykwydchykyn on 2009-03-18
> **ubuwatson said:**
> 
Opening applications seems slow, there is often a delay when opening a file (like a picture) and the overall feeling is that the OS 'seems' sluggish. 

Is preload installed?  Any errors in /var/log/preload.log?

Is there excessive disk activity when you launch an application?

---

### Post by ubuwatson on 2009-03-18
> **lykwydchykyn said:**
> You may have to be more specific about what sorts of things are slow.  I assume you've watched the output of "top" while working, to see if anything's eating up resources?  Are you sure the processor is running at full speed?

Without some concrete data it's hard to know what to suggest.

I agree that I am not being specific, but it's rather difficult to put this into perspective.

Opening applications, switching between applications, etc all seem sluggish.  There is a delay before 'items' open, and even with things that are open the performance seems a bit sluggish.

For instance, in Vista I can open up My Computer and the window is on my desktop in an blink of eye.  When I move around from application to application things are rather 'fluid', no delays, no slowdowns - on the other hand Ubuntu runs as if I am on a slower processor (or something of that nature) - don't get me wrong, Vista has it's own quirks, but still feels faster overall in day to day operation.

The machine has 3 gigs a ram, dual cores, 250 g hard drive, dedicated 256M Nvidia 8400 GS - it's quite a speed demon with other OSs....so I am lost....

People tell me to try other window managers, but why do I need to try a window manager designed to make a machine faster under older hardware when my specifications are more than enough to drive even a bloated OS like Vista ?

---

### Post by ubuwatson on 2009-03-18
> **lykwydchykyn said:**
> Is preload installed?  Any errors in /var/log/preload.log?

Is there excessive disk activity when you launch an application?

I am at work, so I will have to check the log when I get home.  I am not using any preloader for caching of applications unless 8.10 uses on by default.

---

### Post by Helios1276 on 2009-03-18
> **phr0ze said:**
> It seems to me you are saying file operations, or better, nautilis performance is slow. I notice if I double click a picture in nautilis I have a bit of a delay too as the default viewer spins up.

Load xfce desktop for fun and see how that performs.

He should not need xfce with those specs though, @ OP : in the terminal run 'top'. It might show something eating resources.

---

### Post by ubuwatson on 2009-03-18
> **Helios1276 said:**
> He should not need xfce with those specs though, @ OP : in the terminal run 'top'. It might show something eating resources.

I watched processes carefully under the system monitor and didn't see anything out of the ordinary.  Ubuntu was barely using more than 200m of my 3 gigs of ram.  Both processors always stayed in the middle to lower ranges (never maxing out), disk activity seemed normal as well.  Even when running XP under virtualbox, the system performance monitor showed things to be rather neutral and never taxing.

---

### Post by adamlau on 2009-03-18
Don't ask why, just try another WM. Something along the lines of pekwm with Thunar and xfce4-panel.

---

### Post by Helios1276 on 2009-03-18
@ OP Personally, I would want to solve the problem.My specs are near identical to your's and everything is fine. However, changing WM might help and would be interesting to see if it does solve the issue from a troubleshooting perspective.

---

### Post by philinux on 2009-03-18
Have a look in the system logs for anything odd.

/var/log/messages is a good place to start.

Or if you like System>admin>system logs.

---

### Post by phr0ze on 2009-03-18
> **Helios1276 said:**
> @ OP Personally, I would want to solve the problem.My specs are near identical to your's and everything is fine. However, changing WM might help and would be interesting to see if it does solve the issue from a troubleshooting perspective.

I like your progression from not agreeing with me to eventaully making the exact same recomendation.

I recomended XFCE, obiously not because he has a slow machine, but rather to isolate the problem to the WM or something else.

---

### Post by Helios1276 on 2009-03-18
> **phr0ze said:**
> I like your progression from not agreeing with me to eventaully making the exact same recomendation.

I recomended XFCE, obiously not because he has a slow machine, but rather to isolate the problem to the WM or something else.

You did not make yourself clear, at least to me. Well no harm no foul.

---

### Post by fieroboom on 2009-03-18
There are 101 possible reasons your machine is slow, but trouble-guessing won't help any of us. ;)

First thing to do is run top as already suggested, and see what, if anything, is eating up resources. On my last gnome install, I put a nice little graphical CPU monitor on the upper panel, and it was fairly good at showing possible issues, because sometimes when it's already bogged, opening a terminal to run top can seem to take ages. Don't quote me on it, but I believe I right-clicked on the panel, selected to "Add new item" from the menu, and the monitor was right there in the list.

Also, for a terminal, I was turned on to yakuake some time ago, and now it's the first additional program that gets installed after any fresh OS install for me. It's a KDE native, but so far has worked flawlessly in both gnome & Xfce. If you've ever played any of the Quake series (or any other game that had a drop-down command console), then you'll definitely appreciate the usefulness of yakuake.

Also, I'd like to see what specs your laptop has, so run these commands and copy/paste the output here if you don't mind:
```

egrep 'Total|Active|Free' /proc/meminfo

cat /proc/cpuinfo

cat /proc/diskstats
```

:D
-Paul

---

### Post by lykwydchykyn on 2009-03-18
What's your swap utilization look like?  You can find this in "top".

If it's more than a few MB, you might benefit from turning down swappiness.  You shouldn't be swapping anything with 3 GB of memory.

---

### Post by ubuwatson on 2009-04-02
Problem Resolved

I downloaded the very latest Nvidia drivers for linux and installed them.  My machine is now fast, much faster than Vista.

By process of elimination I did the following:

Installed 8.10 fresh - Performance was normal
Installed all system updates - Performance was still normal
Used Ubuntu Recommend 3rd Party Nvidia driver - Performance was slow.
Installed Nvidia driver from Nvidia's website - Performance was better than normal.

---

