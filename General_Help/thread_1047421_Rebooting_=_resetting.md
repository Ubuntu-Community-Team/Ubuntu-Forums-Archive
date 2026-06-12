---
title: "Rebooting = resetting?"
date: 2009-01-22
forum: General Help
---

### Post by bben on 2009-01-22
I'm getting a little bit annoyed right now.

I installed lampp and it ran a perfect localhost.
When I reboot it seems like another version of apache is starting before the lampp one starts. When I try restarting lampp it says that apache is already running, I didn't ask for that to happen, I just installed lampp and added it to the startup document (whatever it's called, it's impossible to find anyway)

Then, I configured my sound (very painfull process) and finally got everything working, it played all music and video files perfectly (even in firefox !) I reboot and guess what? Right, no more sound.

Not only that, but it seems like all I'm doing lately is configure stuff, I log in and all the hours I spent last night getting everything set up just right are lost. I switched to Ubuntu because I thought I'd get more work done instead of solving trojans, adware and virusses. But it seems like it's better to spend 30 minutes scanning your drives than spending 2 hours every day trying to fix bugs.

It's not the first time I've tried ubuntu, and it wouldn't be the first time I give up on it either. For someone who's used to 'the other' OS the learning curve is just too steep.

Anyway, any tips on why my config is messing up every time I boot and where can I find the file that has the startup commands for software at boot? I don't have a clue where to start looking for it, but I need to remove the other apache version from it.

---

### Post by pennacook on 2009-01-22
take a look at /etc/rc2.d for this. Anything with an S starts in run level 2. It might be there isn't a startup script in /etc/init.d that is linked here, so it doesn't start on boot.

---

### Post by mcduck on 2009-01-22
How did you install lampp? If you installed it from repositories it installs as system service (like any server software should). You don't need to (and should not) try to configure it to start yourself. That would just cause it to try to start twice. Just remove the entry you made yourself, you should definitely know where you made your own changes.. ;)

For the other problems, you really need to tell us what you configured, and how.

To me it sounds like you are trying to make things harder way than what's necessary.. :)

---

