---
title: "can't add app to Unity Laucher via vnc4server"
date: 2012-05-16
forum: Desktop Environments
---

### Post by gmoore777 on 2012-05-16
From a 32-bit PrecicePangolin laptop running a vnc client (RemoteDesktopViewer), I am connecting to a vnc4server running
on a 64-bit PrecisePangolin machine. (virtual machine running under Xen 4.1).

When I connect via VNC, I can see the Unity launcher and top menu bar.
But if I try to drag an application from the Dash/Search application
to the Unity launcher, it doesn't stick.
I can't add an App to the Unity Launcher.

But I am able to right click an icon in the Unity Launcher and choose
"Unlock from Launcher" successfully.
So I am able to delete Apps from the Unity Launcher.
(the deletion is persistent on the actual Console after logging out then 
 back in again.)

FYI: I have the same results when going from a 64-bit LucidLynx RemoteDesktopViewer client, to the 32-bit vnc4server PrecisePangolin laptop.

FYI: I am able to connect to a 64-bit vnc4server LucidLynx machine
and add an application to the quick launch section on the top menu bar
which is also noticable on the real Console of that machine (after logging in and then out).
I thing that is a comparable test that shows the console should be alterable via VNC.


Summary: Can anyone change the Unity Launcher on PrecisePangolin
 via any VNC Server product (preferably vnc4server).

---

### Post by gmoore777 on 2012-05-22
I just logged this as a bug [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1003141](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1003141).

---

