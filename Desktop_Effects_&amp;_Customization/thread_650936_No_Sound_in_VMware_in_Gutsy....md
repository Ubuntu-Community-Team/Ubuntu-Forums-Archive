---
title: "No Sound in VMware in Gutsy..."
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by Krucifixation on 2007-12-27
The goal was to play Valve games in WinXP... No problem except that there is no sound. Does anyone know of a VMware Guide with an eye towards running WinXP in Ubuntu??? Sorry if this isn't the right place for this post....

- Kell

---

### Post by mathenge on 2007-12-27
> **Krucifixation said:**
> The goal was to play Valve games in WinXP... No problem except that there is no sound. Does anyone know of a VMware Guide with an eye towards running WinXP in Ubuntu??? Sorry if this isn't the right place for this post....

- Kell

In vmware sound is not available by default. To enable sound, click on "VM" in the VMware console menu, then select "Settings" from the drop-down menu. Set the sound to "Auto Detect."

That should do it.

There are cases where you start your XP virtual machine and it cannot connect to /dev/dsp (the sound device). In my case, this is normally because Firefox has locked this device so when the virtual machine starts it cannot access the sound card (through /dev/dsp). What I have to do is shut down Firefox and then to to VM > Settings to tel VMware to re-detect it. If this doesn't work, then I open a terminal and find out if Firefox is still locking /dev/dsp. The command to do this is:

fuser -muv /dev/dsp

This will also give me the process ID of Firefox and then I can kill it using

kill -KILL <PID>

Where <PID> is the process ID of Firefox.

Hope that helps you.

---

### Post by Krucifixation on 2007-12-27
Thank you Sir, that was quick and painless... I had to actually ADD a sound device first but it was on Auto-Detect and Connect at Power-On by default. I booted XP and the Found New Hardware bubble came up for a moment (Windows runs MUCH faster in the virtual world!) and I was good to go... I had to get to the mixer through the Start Menu but it was a small price to pay... now onto Valve! Again Thank you...

---

### Post by mathenge on 2007-12-27
You're absolutely right. You have to ADD the sound device. I completely forgot that step. I'm glad you got it working and that you're happy running XP in a virtual machine.

I'm also running XP and W2K in a virtual machine and they're behaving really well. I had some issues with USB ports but they all seem good!

All the best.

---

### Post by mohtasham1983 on 2008-02-10
How do you enable your sound card in vmware? I cannot see any option for my sound card in vmware setting.

---

