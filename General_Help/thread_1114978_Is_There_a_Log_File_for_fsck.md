---
title: "Is There a Log File for fsck?"
date: 2009-04-03
forum: General Help
---

### Post by Anlace on 2009-04-03
This morning when I booted up my computer I was greeted with a black screen instead of my desktop in Kubuntu.  The only change that occurred recently was an update to xorg for intel video drivers (which I do not use, I assume that it's a default xorg installation. I have the Nvidia 180 driver installed through jockey).

Here is how I "fixed" the problem.

Upon rebooting the system for the gazillionth time this morning it went into its regular fsck routine and after that rebooted into my much welcome desktop. HURRAY!

Then the power went out. When power came back and I rebooted I had a black screen again.

I used a GParted Live boot CD to run a check on /root and /home and sure enough when I rebooted there was my desktop as it should be.

So now I have a question:

Is there a log file that I can view so I can see exactly what was repaired with fsck? I am concerned about bad sectors on the HD or corrupted files and would like to see exactly what happened to cause/repair this issue.

Thanks for the help.

---

### Post by Anlace on 2009-04-03
Good Morning,

I know this isn't really the forum for this question but it got buried in General Help . . . . .

This morning when I booted up my computer I was greeted with a black screen instead of my desktop in Kubuntu. The only change that occurred recently was an update to xorg for intel video drivers (which I do not use, I assume that it's a default xorg installation. I have the Nvidia 180 driver installed through jockey).

Here is how I "fixed" the problem.

Upon rebooting the system for the gazillionth time this morning it went into its regular fsck routine and after that rebooted into my much welcome desktop. HURRAY!

Then the power went out. When power came back and I rebooted I had a black screen again.

I used a GParted Live boot CD to run a check on /root and /home and sure enough when I rebooted there was my desktop as it should be.

So now I have a question:

Is there a log file that I can view so I can see exactly what was repaired with fsck? I am concerned about bad sectors on the HD or corrupted files and would like to see exactly what happened to cause/repair this issue.

Thanks for any help.

---

### Post by damis648 on 2009-04-03
Check out the /var/log/fsck/ folder. :popcorn:

---

### Post by Anlace on 2009-04-03
Thank you so much for taking a few minutes to answer a simple question :-)

Interestingly enough both logs say "Clean".

---

### Post by plucky on 2009-04-03
Use this to check the fsck log file ```
cat /var/log/fsck/checkfs
``` but I doubt it will have what you want if you ran fsck from the Live CD.This is the file to check if fsck fails when you are booting.

As to why fsck fixed your desktop,I have no idea.(Coincidence!!)


Good Luck

---

