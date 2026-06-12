---
title: "Error starting the GNOME Settings Daemon"
date: 2008-07-06
forum: Desktop Environments
---

### Post by sofasurfer on 2008-07-06
I just booted up and received this message as the desktop loaded...

```
There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply,
the message bus security policy blocked the reply, the reply timeout expired, or the network
 connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

This is the first time I have seen (noticed) this message. However, yesterday I lost my trash icon and my volume control icon after messing with my audio while trying to follow the 'pulse/audio fixes' thread in the multimedia forum.

I fixed the trash and volume icon problem by running 'sudo apt-get install --reinstall gnome-applets'.

Any idea what the above error is all about? So far things seem to be running fine.

---

### Post by lisati on 2008-07-06
I've occasionally had that message about the settings daemon too, but everything seems to be fine. Keep an eye on it, see if it comes back. For me, it was more of an annoyance than an actual problem.

I might be mistaken (and thus open to correction) but I don't think you need worry too much unless it pops up regularly when you boot.

---

### Post by computer_freak_8 on 2008-07-14
I have that same error message every time I log in!

Everything looks weird - all icons are changed to different settings, including the ones on the top and bottom bars.

I have to wait about five minutes (not exaggerating) for it to go from the light tan screen (with a pale rectangle where the error message will soon show) to the messed-up icons screen (which shows my desktop). 
Then, I have to wait *another* three to five minutes (literally) for it to make the login sound and restore all the icons to how they should be. 

I started having this problem a while back, it used to be that I could just reinstall the nVidia driver and it would work another few times without issue (but then after those few times I'd have to do it again). Now it does it every time, no matter what. (The same thing happens whether it is reboot, logout/login, or [Ctrl]+[Alt]+[Backspace].)


Any ideas to keep me waiting ten minutes after I type in my password?

---

### Post by computer_freak_8 on 2008-09-22
> **computer_freak_8 said:**
> I have that same error message every time I log in!

I figured out that my problem was caused by installing the Nvidia driver via EnvyNG.

---

