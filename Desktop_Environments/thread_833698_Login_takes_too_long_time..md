---
title: "Login takes too long time."
date: 2008-06-18
forum: Desktop Environments
---

### Post by rich.bae on 2008-06-18
Hi there.

I'm using Ubuntu Hardy Heron (8.04)
But I have two of login related problems.
First, Login takes too long time. I don't think that is not because of the gdm. However, booting time dose not takes so long time like it. 
and my HW is not so old. I use core2duo 2.4GHz.
and another problem is the re-login. when I re-login means login after logout, I can't login again. at that time, I usally reboot my PC :-(.
after I reboot my PC, I can login eventually.
What's the problem? How do I know the reasons?
Thanks in advance.

P.S. Sorry for my poor English.

---

### Post by xunil54 on 2008-06-19
The first thing i would check would be drivers. then i would say go into the gnome session manager, and see what un-nessicary programs start up automatically. Also be sure to run your updates. If none of that works, then i would say to reinstall the ubuntu-desktop package, or redownload the ISO of 8.04 and run a reinstall. It could have been a bad ISO. I have run into that issue in the past. But most defiantly check your drivers.

If any one else has more input on this topic, i myself would like to know as well.

---

### Post by Lamukra on 2011-09-15
I had problem with login time also but it is already in 11.04, reason was in xorg.conf file configuration
Problem was coming from synaptics touchpad, where the special .conf file was created to make a scrolling work.

Below is outtake from launchpad bug report my comment, how I made scrolling work
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543)

> It was annoying to be without scrolling, so created a file with name psmouse.conf in:

/etc/modprobe.d

with text inside:

options psmouse proto=imps

Saved and run through commands:

```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

After this my ALPS is detected as ImPS/2 Generic Wheel Mouse, but scrolling is working

After making this, I totally forgot about xorg.conf, that I had a Section InputDevice with assigning a driver to my touchpad, what was creating and error, because after making scrolling to work my touchpas was recognised as imPS2 mouse, but not as Synaptics Touchpad... so it was causing the long LOGIN time, not boot time

X was trying to find Synaptics Touchpad but there was imPS assigned Physically, so this so to speak searching time made an interface to stuck...

Solution

Simply comment out Section InputDevice and InputeDevice in Server Layout in xorg.conf

It solved the problem in my case, hope it will help someone

---

