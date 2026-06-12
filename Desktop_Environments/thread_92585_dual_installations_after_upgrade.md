---
title: "dual installations after upgrade"
date: 2005-11-19
forum: Desktop Environments
---

### Post by missmoondog on 2005-11-19
i asked this once, kind of, as part of a 2 part question. i can't find that thread now, thought i subscribed to it. 

anyway, after i upgraded from 5.04 to 5.10 via cd, i wound up with 2 kernel versions loading up at boot up, the 5.04 and 5.10, along with my xp pro. i edited the boot script so that the old kernel version no longer shows up, but are there actually to ubuntu installations on my system? i can't tell from the amount of free space i still have. forget what i had to start with!! if there are 2 installs, is there a way to remove the 5.04 without foobarring everything? 

thank you
subscribing this time

---

### Post by iH8forcedRegistration on 2005-11-20
There aren't two completely different ubuntu installs on your system, just two different kernels and module sets. It's basically like having a C:\Windows and C:\Winnt folder that share a program files directory.

You can get rid of the extra kernel and module set through Synaptic. Open it up, then search for 'linux-image.' Have synaptic remove whichever is older, and then your older kernel will go away. This shouldn't effect the newer kernel in any way.

Just a tip, though, it's sometimes a good idea to have an older kernel version available on your system. For example, my graphics drivers invariably break every time I upgrade my kernel, so I boot to an old kernel long enough to fix the new one. Think of it as a sort of safe mode.

---

### Post by missmoondog on 2005-11-20
thanks for the reply. that's exactly what i thought about the 2 installations. might just leave it alone for the exact reason you state too. i've seen other complaints on these forums about what  you say upgrading the kernel.

edit:
i thought i had upgraded all of my machines. got on this one this morning, still 5.04. figured i had everything down now on doing the upgrades after having done 4 of them this week. upgraded from the cd through synaptic again. second time doing it this way. worked absolutely flawlessly. followed the above advice on the extra kernel being listed (just to see what it did). there was only 1 instance of it listed when i searched. removed it. rebooted. 5.04 is not listed and everything is runnning as sweet as heck!!

---

### Post by swimmaster on 2005-11-22
I am also a newbie.  When I upgraded to 5.10, the two kernels showed up but I lost the option to boot in to my xp disk.  Can anyone tell me how to recover it?

14 hours later:  Never mind - I was able to find support on how to edit the grub list. Thanks Ubuntu forum.

---

