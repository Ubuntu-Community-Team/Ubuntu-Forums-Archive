---
title: "KDE falls asleep spontaneously--suspend problem"
date: 2014-05-22
forum: Desktop Environments
---

### Post by Peter_Brandon on 2014-05-22
I installed KDE on top of Ubuntu 14.04 and *really* like the environment.  One headache, though, is that KDE, or at least my installation of it, seems to have some problems with sleep.  These problems do not occur when I'm using Unity, so am guessing they have something to do with KDE.

One problem is narcolepsy--the system just falls asleep.  Often, I'm just watching a show, so my hands aren't on the keyboard.  The system just suddenly turns off.  Monitor is down, I don't hear the fan, and then a second later it wakes up and I have to log back in.  I've captured some of the system log messages from my latest experience with this:

```
#System Log
#System falling asleep:
05/22/14 06:41:23 PM    GhostWheelLap    kernel    [21888.587954] [drm] Disabling audio 0 support
05/22/14 07:14:00 PM    GhostWheelLap    anacron[12429]    Anacron 2.3 started on 2014-05-22
05/22/14 07:14:00 PM    GhostWheelLap    anacron[12429]    Normal exit (0 jobs run)
05/22/14 07:14:01 PM    GhostWheelLap    kernel    [23847.844527] PM: Syncing filesystems ... done.
05/22/14 07:14:01 PM    GhostWheelLap    kernel    [23848.159594] PM: Preparing system for mem sleep




05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.178339] smpboot: CPU 5 is now offline
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.179775] kvm: disabling virtualization on CPU6
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.222391] i2400m_usb 2-1.5:1.0: timeout waiting for reply to message 0x5606
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.222396] i2400m_usb 2-1.5:1.0: Failed to issue 'Enter power save' command: -110
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.282444] smpboot: CPU 6 is now offline
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.282870] Broke affinity for irq 20
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.282875] Broke affinity for irq 44
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.282877] Broke affinity for irq 45
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.282878] Broke affinity for irq 46
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.282881] Broke affinity for irq 48
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.282884] Broke affinity for irq 50
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.283895] kvm: disabling virtualization on CPU7
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.386555] smpboot: CPU 7 is now offline
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.387942] ACPI: Low-level resume complete
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.387984] PM: Restoring platform NVS memory
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.388490] CPU0: Thermal monitoring handled by SMI
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.388534] Enabling non-boot CPUs ...
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.388569] x86: Booting SMP configuration:
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.388570] smpboot: Booting Node 0 Processor 1 APIC 0x1
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.399634] CPU1: Thermal monitoring handled by SMI
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.399664] kvm: enabling virtualization on CPU1
05/22/14 07:14:09 PM    GhostWheelLap    kernel    [23850.402037] CPU1 is up



```

Looks like anacron or the file system syncing immediately after anacron runs triggers the falling asleep.  Around 7:14:09, the system realizes that the sleep wasn't properly triggered and everything begins to wake up again.

Any thoughts on how I can figure out what's up?

Peter

---

### Post by Zorael on 2014-05-23
Have you checked your Energy Saving profile? It's in the Hardware section of System Settings.

[img]http://i.imgur.com/eTnoGLI.png[/img]

Ugh, that turned out huge.

[Edit] Additionally...
> **Peter_Brandon said:**
> Looks like anacron or the file system syncing immediately after anacron runs triggers the falling asleep.  Around 7:14:09, the system realizes that the sleep wasn't properly triggered and everything begins to wake up again.
I imagine that's just part of the standard teardown; an effect, rather than a cause. Save state, sync disks, enter sleep. You should see the same thing happening if you trigger a deliberate sleep.

---

### Post by Peter_Brandon on 2014-05-23
Thanks Zorel!  Interesting hypothesis.  I'm on AC power, and my system suspend box is unchecked.  On the other hand, 'Screen Energy Saving' is checked, so maybe there's some bug w/ that.  I've unchecked it and I guess I'll see.

When I deliberately trigger suspend, my system does something like what it does when it spontaneously falls asleep--it suspends and, about half the time, wakes right back up.  It usually stays suspend the second time I try.  Odd.

Peter

---

### Post by Peter_Brandon on 2014-06-07
Unfortunately, changing my power settings didn't fix the problem, and my suspend problems are getting worse in some respects.

Despite the change to 'Screen Energy Saving,' my system spontaneously suspends while I'm, say, working on a text file or while I'm watching a show.  So, it's not my activity level that's triggering it.

Since some of the resent updates, the sudden suspends and the system freeze when I suspend are occurring less frequently, but at least the former is still occurring.

One thing I've noticed lately is that the system spontaneously falls asleep every time I switch activities.  I can wake it up again without problems, but this does rather limit my ability to use activities.

I wonder, given that I haven't seen much online about this problem, whether it may have something to do with the peculiarities of my install--say that I added KDE after installing Ubuntu.  I also always see an error message about hal, which I installed in order to view Amazon videos.

If anyone has any clues, I'm all ears.

---

### Post by SeijiSensei on 2014-06-08
I've run KDE for well over a decade and never encountered this problem.  It sounds like a hardware issue.

Have you run memtest?  Have any overheating problems?

If it's not a hardware problem, I'd consider reinstalling but use the [Kubuntu 14.04 DVD]("http://cdimage.ubuntu.com/kubuntu/releases/trusty/release/") instead of adding KDE on top of Ubuntu.

I believe I have watched Amazon Instant via [pipelight]("http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html") without HAL installed.  Now I have a TV with apps built-in so I haven't tried using Linux with Instant for a while.

---

