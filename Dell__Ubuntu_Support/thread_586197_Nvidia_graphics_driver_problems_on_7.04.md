---
title: "Nvidia graphics driver problems on 7.04"
date: 2007-10-22
forum: Dell  Ubuntu Support
---

### Post by Carl Foxmarten on 2007-10-22
I'm currently using Ubuntu on both a desktop computer and a laptop and the last version I've used was Dapper, which worked perfectly with the Nvidia graphics cards in both the laptop and the desktop.

I've switched to Feisty on both, as it works so much more smoothly than Dapper did (I haven't tried Edgy yet, I kind of skipped it).

My problem is that the "nvidia-glx" package doesn't work on my laptop (Dell Latitude C840), and the "nvidia-glx-legacy" package doesn't actually give me the GLX extension that I need to use Blender.

Can anyone give me any suggestions as to how this problem could be fixed?

(Kernel version: 2.6.20-16-generic, nvidia-glx version: 1:1.0.9631+2.6.20.5-16.5-16.29, I can give post version numbers for anything else you'd want to know if asked)

Thanks,
Carl.

---

### Post by ofb on 2007-10-22
I see there's an open bug that may be relevant.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/82312](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/82312)

---

### Post by Carl Foxmarten on 2007-10-22
After poking around a bit more, I found out that the graphics card I'm using (GeForce 440 Go) is only supported by the nVidia driver version 96xx and earlier, and it's not getting properly detected.

While the nvidia-glx-legacy package works, it doesn't support GLX and the Composite extensions at the same time (which would be nice, but not ultimately required and I did manage to disable Composite, so I'm okay for now).

Thanks for the link to the Launchpad bug report, I managed to find some interesting and possibly helpful information there.

---

