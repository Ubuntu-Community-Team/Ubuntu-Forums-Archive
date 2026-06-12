---
title: "computer keeps crashing at boot"
date: 2016-09-17
forum: Desktop Environments
---

### Post by starcry on 2016-09-17
Hello,

My computer is doing weird things and I'm not sure where to go to see the cause so I can fix it.

It doesn't happen every time but sometimes at boot the system hangs and I have to do a hard reboot and then run fsck on /dev/sda1. I have to do this many times and it can take up to 30 minuites for me to get booted up. Then sometimes my browser will crash and exit and I have to do a full reboot to get it back. 

I've checked the logs but I'm not entirely sure what I'm looking for or where to start.

Does anybody have any suggestions?

---

### Post by DuckHook on 2016-09-17
Your problem may be HW and not the OS.

First, describe your HW completely. It is difficult to advise without good info. See the link in my sig: *How to Ask for Help*

Things to check:

[LIST=1]
[*]Disk health. Post back results of:```
sudo smartctl -H /dev/sda
```
[*]RAM health using memtest86+ by choosing memtest at your next boot. Caution: memory testing can take a long time, depending on your amount of RAM.
[*]PSU for dependable, unvarying power. A failing PSU causes all sorts of strange behaviours that are very vexing because they seem random and inexplicable.
[*]It could also be a cracked/failing MOBO which creates random faults similar to PSU.
[/LIST]
Try running from a LiveUSB/DVD to see if problems persist. If they do, then problem is likely HW. If the LiveUSB/DVD runs reliably, then the problem may be a corrupted OS. This can be caused by bad disk sectors, a bad update file or installation of non-repository apps.

[LIST=1]
[*]Do you use PPAs? If so which do you have installed?
[*]Have you installed any software from outside of the repos?
[*]When did you last update your OS? Any unusual events/messages?
[/LIST]

---

### Post by Bucky Ball on 2016-09-17
As above. What is on sda1??? Windows, if a dual-boot?

---

