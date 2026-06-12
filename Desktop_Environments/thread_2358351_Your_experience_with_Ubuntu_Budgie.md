---
title: "Your experience with Ubuntu Budgie?"
date: 2017-04-12
forum: Desktop Environments
---

### Post by veddox on 2017-04-12
Hi everyone,

I've just learnt that Ubuntu Budgie is an official flavour now. As I am not a fan of the GNOME shell, I've been thinking about what DE to switch to when Canonical dumps Unity. (I know that isn't going to happen right now, but one can plan ahead...)

I like the look of the Budgie desktop, but wanted to hear from users what they think of it? Especially with regards to its stability, as it's still a pretty new DE.

Thank you very much :-)

---

### Post by Frogs Hair on 2017-04-12
I've had no problems , though I run it as second desktop on 17.04. The full desktop which I tried yesterday has some different default applications, but I'm thinking it will be my DE in 18.04 cycle. I suggest downloading the ISO when Ubuntu Budgie is released and try the live session. You can try it now of course. ;)

---

### Post by ajgreeny on 2017-04-12
I tried it just as a VM in VBox, and it worked fairly well for me, though I did not like budgie much as a DE.  That may simply be down to its newness and, to my eyes, lack of polish, but I shall certainly try it again at some point in the future, perhaps even again soon.

PS: Very minor thing as I usually change the desktop wallpaper, but I did like the budgie default very much indeed, and have kept it as a wallpaper on other of my systems using alternative DEs.

---

### Post by qyot27 on 2017-04-23
So far I've only been able to get it to run from a 64-bit Live USB and a 32-bit VM.  Trying to install ubuntu-budgie-desktop into my current 64-bit install or fresh installing from the aforementioned Live USB, while the download/install process worked without issue, it won't let me log in.  I enter my login credentials, the screen looks like it's going to start Budgie, but then drops me back to the log in screen (or it managed to get partially into Budgie, but not enough for the panel, Plank, and virtually anything else to load, forcing me to hard reset just to get out).  I'm not sure what's causing the problem, more than likely it's something in my .config area (since the VM and Live USB both worked), but I don't know what it could be.  Also, at least in my normal LXDE session, Plank started showing up and LXPanel bugged out, with no way to fix it short of another fresh install to set it back.  Maybe if I'd installed ubuntu-budgie-desktop using aptitude rather than a normal apt-get install it would've sandboxed it enough to make sure that didn't happen, but I dunno.

I certainly like the look of it, though, and would have spent time evaluating whether it was something I'd prefer to use in lieu of Gnome when 18.04 arrives.  I just can't seem to do so right now.

---

### Post by vasa1 on 2017-04-23
> **qyot27 said:**
> ...  I'm not sure what's causing the problem, more than likely it's something in my .config area (since the VM and Live USB both worked), but I don't know what it could be.  ...
You could test that by temporarily renaming your ~/.config folder to, say, ~/.config.bak. Then log out and try Budgie. A new ~/.config would be created by the system. 

If things don't work and you need to hard reset, you'll know the problem wasn't with your ~/.config. Reboot into a desktop you know works, delete the existing ~/.config and rename ~/.config.bak to ~/.config.

If the Budgie session works, you'll have to figure out what in your ~/.config caused the issue.

---

### Post by qyot27 on 2017-04-23
> **vasa1 said:**
> You could test that by temporarily renaming your ~/.config folder to, say, ~/.config.bak. Then log out and try Budgie. A new ~/.config would be created by the system. 

If things don't work and you need to hard reset, you'll know the problem wasn't with your ~/.config. Reboot into a desktop you know works, delete the existing ~/.config and rename ~/.config.bak to ~/.config.

If the Budgie session works, you'll have to figure out what in your ~/.config caused the issue.
I also tried running a Guest session, but that didn't work either.  I can't remember if that was the instance of it only partially loading, or if it was another case of dropping me back to the LightDM prompt.  I didn't keep notes while trying it.

I mean, maybe it had to do with the graphics drivers rather than ~/.config.  Live environments can take the liberty of running drivers that may not be enabled after install, right?  This would be the whichever version of the Intel graphics drivers and/or kernel support* are needed for Bay Trail-T/Silvermont.

*since I also have to use kernel version 4.11 to make audio work through HDMI here.  But even when I tried using 4.10 as shipped with 17.04, it didn't solve the issue.

---

### Post by qyot27 on 2017-04-30
After going through almost a week of retesting things, it's not .config.  Not completely, anyway.  I eventually got so frustrated that I did a completely clean install on a completely new partition - same problems.  It's something about the hardware doing it, even though the Live session runs without error.  When installed on real hardware (well, USB flash drive), it hangs on underlying parts of the system during the login process, and in the event it shoots me back out to the LightDM prompt and I tell the machine to shutdown, it takes 6-7 minutes to do so, taking its own sweet time to disengage the Network Manager, and then after getting everything shut down, not actually shutting off the power, forcing me to power off manually.  Again, the Live environment goes through shut down in seconds and powers off the machine properly.

Interestingly, on an old Athlon64 machine, these issues never occurred (but Budgie is too graphics heavy to run smoothly on that setup).

So I dunno.  I'm hoping it's just a peculiarity of this mini-PC and that when I build a conventional setup later on this year or next year that this issue resolves itself.

---

### Post by jpberes on 2018-04-03
I am using Budgie now for over 3 months on Ubuntu 17.10 and this without whatever problem...
Nice not heavy on resources and very stable ;-)

---

### Post by DuckHook on 2018-04-03
Please do not necromance dead threads. This one is almost a year old and was due for automated closure in but a few days.

Thread closed.

---

