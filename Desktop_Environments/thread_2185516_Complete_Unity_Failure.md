---
title: "Complete Unity Failure"
date: 2013-11-03
forum: Desktop Environments
---

### Post by Linux-sgt on 2013-11-03
Hello all, I have had a serious problem that I would rather not solve by re-installing my OS... although perhaps this may be the only option.

I am running 64bit 13.10 on a 2.6Ghz 16GB laptop, no issues there. I recently installed VirtualBox. As soon as I did so, I noticed terminal disappeared from my task bar. I rebooted, logged in - and, horror of horrors, I only saw my desktop and its 3 resident files. None of my hot keys work, can't start up terminal, unity is completely broken.

Does anyone have an idea how to either, a) completely repair unity from recovery mode terminal, or b) know any other way to resume regular function without a complete reinstallation of ubuntu...

I humbly await the collective knowledge of my superiors,

Jon

---

### Post by Linux-sgt on 2013-11-03
So, while I typed the original post from another machine, I went through root terminal in recovery mode, and tried to see what was going on with unity. Turns out IT WAS REMOVED... What evil? I installed it from terminal, rebooted, and I am back into the machine and can navigate a GUI, but I can no longer access terminal! All that is left is xterm... What in the world has virtualbox done?! Any help with this fresh batch of hell would be appreciated.

Jon

---

### Post by Linux-sgt on 2013-11-03
Commence embarassment. Apparently, that install of VirtualBox screwed something up, killed unity, ubuntu desktop, etc. I fixed the problem - and here's how:

I was always able to log into my account and view my desktop - but I couldn't navigate windows or see anything but three files I keep on my desktop. I used CTRL+ALT+F6 to get into a terminal shell and did the following:

>sudo apt-get remove virtualbox* --purge
>Sudo apt-get update
>Sudo apt-get install unity
>Sudo apt-get install ubuntu-desktop
>Sudo reboot

And VOILA! I can't believe it was as simple as this - but the simplicity is what stumped me. I would never have guessed **installing** *VirtualBox* could **uninstall** *Unity* and *Ubuntu Desktop* all in one shot. Go figure. 

Sufficient to say, I will not be reinstalling nor recommending VirtualBox for a long time.

Hopefully my overlook may help someone in the future.

Jon

---

