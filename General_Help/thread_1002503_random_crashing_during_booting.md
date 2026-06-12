---
title: "random crashing during booting"
date: 2008-12-05
forum: General Help
---

### Post by tetrafuran on 2008-12-05
The computer crashes randomly. This can happen at any moment, but seems to be particularly likely during booting. Some times it takes several re-boots in order to get to the desktop. I'm looking for advice as to what to do next.

** Here's what normally happens**
1) After loading grub I am supposed to see the text "kernel alive", but instead I just get a black screen with a line _ in the top left corner. Nothing happens after that.

2) During the second boot up it might get to actually load ubuntu. It can crahs on any random point during that orange loading bar. Sometimes it lodas normally too.

3) If I reboot immediately after that it's very likely to freeze even before loading the grub. This can usually happen while bios displays information about cpu, ram drives etc. Once again this can happen in any random point while loading bios. Every time that happened, it was before bios allowed me to perss del to enter bios. After that there's no pont to keep on pressing reset, since 3) seems to happen all the time once has done it once.

4) Instead I usually just shut down the computer for a few seconds, allow the hdd and fans to stop and then reboot. This bizare manoeuvre results in a perfectly normal boot up. These are the steps of a ritual I go through in order to use ubuntu. I've done it many times and it works. However 

** My ideas.**
a) Heat
b) Faulty hardware
c) OS
d) kernel

** My attempts so far.**
a) I installed an aditional fan. Nevertheless the CPU core temperature is still above 50C. I suppose error 3) might be caused by heat, but since I cannot measure core tempereture during those seconds it's impossible to say for sure.
b) I have scanned the hard drive with fsck (fsck.ext3 -fyc /dev/sda1). No errors were found. I also scanned my 2GB memory with memtest86 (from ubuntu cd). Fortunately there were no errors either. I kept on rescanning for 42 hours so I'd say the memory is in excellent condition.
c) I have another hard drive which has windows xp installed on it. It boots and works just fine. 3D games can still heat freeze it occasionally (it's the heat no doubt), but no crashes ever happen during boot up.
d) I have tried selecting different kernels from grub, but error 1) keeps occuring.

Edit: I disconnected cd:drives and the problem seemed to disappear. I'm testing other configurations to find out if I can rule out other factors, but at the moment it seems that connecting two cd drives might be the problem.

---

