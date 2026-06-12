---
title: "Disable input device, AutoAddDecices=True"
date: 2010-06-10
forum: Desktop Environments
---

### Post by JohannesD on 2010-06-10
Hi!
I have installed Lynx and want to use two X servers at the same time. Each server has its own ServerLayout section in xorg.cong. The first ServerLayout Section has AutoAddDevices enabled, so that new input devices are added automatically.

The second ServerLayout has AutoAddDevices disabled, and one InputDecice pointing to /dev/input/mouse3. That way, this mouse is the only input decive affecting the second X instance.

Unfortunately, this mouse is also controlling the first server (due to AutoAddDecives). Can anyone tell me how to disable this? I want every input device to be added to the first server, except this mouse.

In earlier versions of ubuntu, I used a hal rule to make hal ignore this mouse. So it was not added to the first server. Now that hal is not used by lynx anymore, I don't know how to do this. I have already read some things about udev and the xorg.conf.d folder, but I could not find a simple solution.

I hope that somebody can help me with this.

Thanks!
Johannes

---

### Post by JohannesD on 2010-06-14
Anyone?

bye,
Johannes

---

