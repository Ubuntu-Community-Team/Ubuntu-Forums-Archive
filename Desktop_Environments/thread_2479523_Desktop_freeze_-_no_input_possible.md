---
title: "Desktop freeze - no input possible"
date: 2022-09-28
forum: Desktop Environments
---

### Post by brad_richards on 2022-09-28
This problem occurs on both my laptop and my desktop, which have very different hardware (e.g., Intel vs. AMD). Both running Xubuntu 22.04.

Once every day or two, the computer will refuse all input. The mouse pointer moves, but you cannot interact with any windows. Keyboard input is not recognized. However, all running programs continue to work normally.

The workaround: Use Ctl-Alt-F1 to switch to console login. After this appears, use Ctl-Alt-F7 to switch back to the graphical interface. This always works, but sometimes it takes a long time (10 seconds or more) for the console login to appear.

I have seen this problem mentioned in other forums (for example, reddit), but I haven't seen it here. Anyone else have the problem? A solution? Ideas?

*ETA: This occurs in the middle of working. It has nothing to do with resuming from sleep, or anything like that. I've had it while playing a game, I've had it while in a Teams meeting, etc..*

---

### Post by TenPlus1 on 2022-09-28
Could you be running out of memory and the system hitting the swap file hard and slowing things down ?  Maybe try a lighter desktop to see if it helps.

---

### Post by ActionParsnip on 2022-09-28
Make sure you have the latest BIOS in the system. This may help

---

### Post by &amp;KyT$0P# on 2022-09-28
I think I may have seen this before on systems that kept xfwm4 as window manager.  But those systems were definitely pre-22.04.  I haven't seen it on my general-purpose systems, which use Openbox under Xfce.

Maybe try installing Openbox and then switching to that as your window manager for Xfce -
```
sudo apt-get install openbox
openbox --replace &
```

If this works and you want to make this persistent, go to Settings > Session & Startup > Current Session, and click "Save Session".

---

### Post by brad_richards on 2022-10-03
Thanks for the replies. The problem occurs so irregularly that experimentation is difficult. BIOS seems unlikely, since the machines are very different (and from different manufacturers). Memory is definitely not the problem (one machine is 32GB, the other 64GB). I will have a look at Openbox.

---

### Post by QIII on 2022-10-03
I have seen this happen in only one circumstance, this on Kubuntu:  When working on a client's VPN (They specified Cisco AnyConnect, for which i used an open source alternative) a few years ago, I would suddenly be able to move the mouse, but be unable to interact with the GUI beyond that.  I pretty much had to do a hard reset.  Eventually, the problem disappeared spontaneously and I was never able to diagnose it.

So I wonder if you might have some background process going on (that you have running on both machines) that burps and throws a tantrum.  Is anything else going on at the time on those machines?  Is your normal workflow the same on both?  Updates, virtual machines, secure connections outside of your local network?

---

### Post by brad_richards on 2022-10-03
Hmmm... Workflow is definitely the same on both machines, it's just a question of whether I'm at a desk or underway. So the same tools are installed. I will try to keep track of which tools are open when it happens, but the irregularity makes collecting data difficult.

---

### Post by QIII on 2022-10-03
Nothing worse than trying to debug/diagnose something that is infrequent and apparently random..

---

