---
title: "No libGL.so found?"
date: 2005-12-08
forum: Gaming &amp; Leisure
---

### Post by siorai on 2005-12-08
I decided to go old school and play some Quake2. I got it installed and starting up find, but I ran into a problem: no 3d acceleration. I see in the console when I try to enable OpenGL that it can't find libGL.so. I do some hunting around on here, find out how to check if the symbolic links are correct, but I don't even have libGL.so on my system at all. What would I need to install to correct this?

I'm running 5.10 with and Nvidia 6800.

---

### Post by professor_chaos on 2005-12-08
you have to install the nvidia drivers
sudo apt-get install nvidia-glx

Do a search on this forum for more detailed info.

---

### Post by Perfect Storm on 2005-12-08
```

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

```

reboot

If it still can't find libGL.so you need to make a symblink.

```
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
```

---

### Post by siorai on 2005-12-09
[QUOTE=Artificial Intelligence]
If it still can't find libGL.so you need to make a symblink.

```
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
```[/QUOTE]

That did it. :D Thanks.

---

