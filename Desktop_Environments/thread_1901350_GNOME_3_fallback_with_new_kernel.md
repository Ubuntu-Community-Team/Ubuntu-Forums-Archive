---
title: "GNOME 3 fallback with new kernel"
date: 2011-12-28
forum: Desktop Environments
---

### Post by emptycoder on 2011-12-28
I have updated my system with Update-Manager and it seems that it upgraded my kernel too, now I have two kernels on my GRUB screen, version 3.0.0.13 under (Previous Versions) and the newest one which is 3.0.0.14
First I chose the newest one but GNOME 3 falls back to GNOME 2 (Classic), I though that I might chose by mistake GNOME Classic in Login Screen but I didn't, both GNOME and GNOME Classic options are the same result.
The only solution I found that I have to choose the old Kernel every time I turn on my computer.
So I was wondering, is there something I'm missing here?
Thanks for help.

---

### Post by 3Miro on 2011-12-28
Fallback mode activates automatically if your video card or video card driver doesn't support 3D acceleration. The new kernel somehow messed up the video driver, it shouldn't happen but sometimes it does.

If you have Nvidia card or you are using ATI proprietary drivers, go to Additional Drivers, deactivate the proprietary driver, reboot, reactivate the driver and reboot again. This should solve the issue.

If you have Intel or ATI default drivers, then you have a more serous bug and I am not sure how to fix it.

---

### Post by emptycoder on 2011-12-28
I'm using ATI catalyst driver, the official one, open source drivers doing no good with GNOME 3, it cause glitch and it's overheating my laptop with no reason.
In my condition, do you suggest to unintsall the driver, then install it back again? or it's a useless move?

---

### Post by 3Miro on 2011-12-28
> **emptycoder said:**
> 
In my condition, do you suggest to unintsall the driver, then install it back again? or it's a useless move?

That is exactly when I think uninstall/reinstall would do the trick. Catalysis needs to add a separate module for each kernel version, those come from AMD and not Ubuntu/Canonical. The update manager should have gotten the module automatically, but sometimes it fails to do so.

Give it a try and let us know.

---

### Post by emptycoder on 2011-12-28
it works like charm! uninstalling and reinstalling the driver fixed the problem, without falling back to gnome classic.
many thanks 3miro, you saved my life.
many thanks.

---

### Post by 3Miro on 2011-12-28
> **emptycoder said:**
> it works like charm! uninstalling and reinstalling the driver fixed the problem, without falling back to gnome classic.
many thanks 3miro, you saved my life.
many thanks.

I doubt it was your life, but I am glad to help. :P

If you don't have any more issues with this, please mark the thread as "Solved", it helps us keep track of things and also for other people that may have the same issue.

---

