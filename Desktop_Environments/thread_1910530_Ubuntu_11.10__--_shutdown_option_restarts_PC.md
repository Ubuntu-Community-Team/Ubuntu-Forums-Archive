---
title: "Ubuntu 11.10  -- shutdown option restarts PC"
date: 2012-01-17
forum: Desktop Environments
---

### Post by shields on 2012-01-17
I've been using Wake on Lan for some time. Recently, I made some changes to grub and about that same time I could no longer shut down my machine from Ubuntu. It just restarts.

It doesn't matter if I type:
[LIST]
[*]```
sudo shutdown -Ph now
```
[*]or if I shutdown from the gui 
[*]or if I let crontab shutdown as it's been doing for months
[/LIST]
I still get the reboot when I try to shutdown the PC.

I can solve this problem by taking advantage of my dual boot, going into Windows, and shutting down from there -- but that's just silly.

Another user resolved this issue by removing Wake on Lan from the bios settings, but I use this feature.

I'd be happy for Ubuntu to just reconstruct grub, if that would solve it, but I don't know how to instuct it to do that. Also, I am not certain that the grub changes caused this issue.

Anyone have any suggestions of a fix?

---

### Post by collisionystm on 2012-01-17
the command is

sudo shutdown -P 0

try that.

---

### Post by shields on 2012-01-17
> **collisionystm said:**
> the command is

sudo shutdown -P 0

try that.

Thanks. That works as good as any other Ubuntu shutdown method..... *it doesn't*.

When I type that in the terminal, the system reboots.

The only way to shut off the computer (shy of removing the power) is to let it reboot to Windows and then have Windows shut it down.

What is Windows doing that Ubuntu is not in its shutdown routine?

---

### Post by shields on 2012-01-17
HA! I fixed it.

I pulled the power cord and let it sit for a few moments and then plugged it in and started it up.

Then I went through a normal shutdown with Ubuntu and it worked.

---

