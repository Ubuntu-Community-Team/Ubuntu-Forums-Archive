---
title: "Memory management issues"
date: 2009-05-21
forum: General Help
---

### Post by lovinglinux on 2009-05-21
I know that unused memory is wasted memory and I agree, but I have issues with memory management since I started to use Ubuntu and I'm not the only one.

The problem is that after a couple of hours using the machine, most of the memory becomes occupied by the cache and performance drops. I'm not talking about freezing or anything like that, it's just not as smooth as when I boot. For example, if I use the "Window picker" and select a window from another workspace, the cube rotates fine but at the end, when the window zooms in, it stutters a little bit. Also Firefox scrolling becomes less fluid and such.

Is not a huge problem, but it's kind of annoying. I tried to find a command to clear the cache, but nothing works. I have a workaround, but is not a solution. I start a virtual machine which uses half of the memory, then close it just after it is loaded properly and discard the current state. Since most of the memory is requested to run the VM, when I close it the memory used by the cache is gone and performance goes back to normal.

I would like to know what could be causing this performance drop and if there is a way to clear the cache without starting a VM?

BTW, I have 2 Gb DDR2 RAM.

---

### Post by lovinglinux on 2009-05-24
There is [another thread](http://ubuntuforums.org/showthread.php?t=1168443) posted today reporting the same issue. I think this is a real issue and I really would like to know a solution. For example, would it be possible to limit the memory used by cache?

---

### Post by lovinglinux on 2009-05-25
> **Greenwidth said:**
> I have not tried this:

HOWTO: Clear filesystem memory cache
[http://ubuntuforums.org/showthread.php?p=3882342](http://ubuntuforums.org/showthread.php?p=3882342)

Thank you. Here is the command:

```
sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

I tried so many commands, but this is the only one that really works. Thanks again.

---

