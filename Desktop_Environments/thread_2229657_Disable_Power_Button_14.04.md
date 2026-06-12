---
title: "Disable Power Button 14.04"
date: 2014-06-14
forum: Desktop Environments
---

### Post by nadarockyraccoon on 2014-06-14
I'm blaming it on the kids, but I also occasionally hit the power button without noticing, wich results in the computer shutting down after 60 seconds. This hasn't been much of an issue, but I'm now running Ubuntu on an acer c720 chromebook. Unfortunately my kids(to young to know better, 18 months) pressed space and then enter on boot which wipes the hard drive. I voided my warranty and set the gbb flags to automatically boot legacy mode, still one second they can ruin everything though. Best solution I have is to make the power button not do anything in a booted os. I've looked as several post describing solutions to this issue, but only one with a resonable solution that unfortunately did not work, seems to be an issue with using parts of systemd with upstart in Ubuntu 14.04.

So far I have tried editing logind.conf to contain HandlePowerKey=ignore with no luck. After digging around I'm not coming up with anything so I decided that fo the first time in years I actually needed to ask for help. So that's what I'm doing, how on earth can I stop the os from recognizing the power button? Many thanks in advance to any that can help.

Also as it seems to make a difference I'm running gnome-session-flashback

---

### Post by nadarockyraccoon on 2014-06-14
And moments later, a solution. I'm guessing this only works with gnome, though from what I gather the conflict is with systemd and gnome sooo
```
sudo apt-get install gnome-tweak-tool
```
in a terminal:
```
gnome-tweak-tool
```
Click the tab labeled Power and select do nothing for Power Button Action

---

