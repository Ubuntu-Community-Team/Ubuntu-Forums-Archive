---
title: "Failed to get D-Bus connection error when trying to start lightdm (desktop)..."
date: 2014-06-08
forum: Desktop Environments
---

### Post by chris231 on 2014-06-08
I've been using Windows only for a little over a week because of this problem.  If anyone can help me, it will prevent me from reinstalling Ubuntu.

My desktop had broken after I installed standard updates for Ubuntu (ie Kernel patches, etc).  I learned that I needed to reinstall the 3rd party drivers (I had an NVidia display driver that was installed in conjunction with a dirver for the Cuda parallel programming API).

At one point I had the desktop running (without icons), but now light dm ceases to start correctly.  The NVidia logo does briefly show up, though on normal start up.

I tried logging in as root in recovery mode (since a lab member at our university told me I'd have to work in this mode) and ran:
```

sudo mount -o remount,rw /      (to make the file system readable, per my lab contact's instructions)
su datahead                     (in order to run the display manager as myself)
sudo lightdm start              (in order to launch the display manager)

```

It has been giving me this error after a while, though:
Failed to get D-Bus connection

I've been searching around on google but can't find any instructions on this error that I can follow.  If anyone can help me figure out exactly what to do, it would be appreciated.  If I can't find a solution, I will have to reinstall Ubuntu.

---

