---
title: "Sluggish performance with Dapper (Breezy was fine)"
date: 2006-09-15
forum: Desktop Environments
---

### Post by QwUo173Hy on 2006-09-15
I've just installed Dapper and upgraded all packages. I've also installed a few programs like Skype, the latest amaroK and kernel2.6.15-23-686.

From time to time, the system gets sluggish and 'stammered'. The mouse movements become jerky. I think that some keys are missed too when I type quickly. Amarok also skips while playing back sometimes.

I have 'top' running in a terminal all the time to try to find out whats happening. It seems that Xorg is the problem. It is always at the top of the list when this happens (along with gam_server).

I didn't have these problems with Breezy so I assume it's fixable. Are there any common causes to this kind of behaviour that I can be looking into? 

Thanks,
J

---

### Post by QwUo173Hy on 2006-09-30
So far, I have pinned things down a little. The problem seems to be one thing. When the system gets sluggish, everything gets jammed for a second or two (audio, keyboard input and mouse).

Sometimes I loose the mouse altogether and I have to do

```
sudo rmmod psmouse
sudo modprobe psmouse
```

To get it back again.

My audio playback is still choppy if the system is doing anything - even non cpu-intensive tasks (like opening a new konqueror window).

I've run top and cant see a clear culprit. I've also run 'ps -A' and killed off any python / ruby things running. I've gone into /etc/init.d and run 'chmod -x' on anything I don't need (like raid, nvidia (I have an ATI), bluetooth etc).

Is there *anything* I can do at this stage? Maybe theres a way I can see beyond the processes and see what actual daemons are running?

I've spent months getting everything working on Dapper, the only thing now is to find what's causing this problem.

Thanks,
Jarlath

<edit> by the way, I'm a laptop user in case that means anything. 850Mhz / 320MB Ram / 7200 RPM harddrive. Breezy ran very smoothly. Audio never skipped, even when I started up numerous heavy weight apps simultaneously (eg Limewire / Openoffice / Firefox)

---

