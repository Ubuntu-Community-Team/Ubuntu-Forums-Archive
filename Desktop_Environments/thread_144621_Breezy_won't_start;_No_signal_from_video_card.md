---
title: "Breezy won't start; No signal from video card?"
date: 2006-03-14
forum: Desktop Environments
---

### Post by sailor420 on 2006-03-14
Hey guys... Hopefully someone here can help me with this. I'm running Breezy, and the other day, it seemingly randomly stopped booting. I say randomly because I didn't install or update or reconfigure anything to my knowledge, and I know that the hardware is working because it will boot Windows or a livecd just fine.

Anyways, the machine turns on, and goes through the splash screen bootup. Then, at the end, when normally the nVidia screen and then the X login screen would come up, I lose signal from the video card and the monitor shuts off.

I've noticed that this happens when something fails during startup--mounting a filesystem, connecting the network interfaces, whatever. But normally, a quick reboot fixes it. This time, however, that isn't working. So my guess is that maybe something isn't starting correctly, though I haven't seen any errors on the screen.

I guess my first step would be to figure out if something was hosed when it tried to boot--how would I do that? Any other ideas of what could cause it?

BTW, the nVidia driver was installed with the Automatix program if that helps.

Thanks for any help...

---

### Post by sailor420 on 2006-03-14
OK, if I boot to single-user mode, it boots, if that helps anyone...

Also, it seems that my /home has some errors that it's having to fix on boot... It says it fixed it, but then comes right back and does it again next boot. Maybe that's part of the problem?

---

### Post by Ramses de Norre on 2006-03-14
What's in /var/log/Xorg.0.log.old?

---

### Post by sailor420 on 2006-03-14
Ramses, do you want that file when I can boot the machine into single-user mode? How much of it would you like?

---

### Post by Ramses de Norre on 2006-03-14
In the file with the .old extension, the messages of the previous login are saved. So open it from single user mode.
I think the errors will be at the end, but you can look after any error messages or strange things.

---

### Post by sailor420 on 2006-03-14
Random update--I disabled gdm on start then started it in multi-user mode (as normal) and started GDM by hand--and it worked. So I re-enabled GDM on boot and now it boots fine. No idea why, but that kinda concerns me, cause I didn't do anything, and I'm worried it'll start to do it again.

Edit--I did notice that it did it's "its been 30 boots, checking filesystem" thing last boot--maybe there were errors that it fixed? It didn't say anything that I saw, but it flew by quickly so I could have missed something...

---

