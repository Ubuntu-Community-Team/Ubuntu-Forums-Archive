---
title: "compiz.real takes up 94% of CPU"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by finer recliner on 2007-12-02
hey guys,

im having a problem where the process compiz.real is taking up 94% of my CPU whenever i close my laptop's display and leave it on overnight. when i open my laptop back up, nothing works except for the mouse, so i do ctrl+alt+f1 and type 'top'. i see that compiz.real is taking about 94% of my CPU, so i have to use kill -9 on it (normal kill doesnt work on it). after killing the process, my computer starts working again. has anyone else seen this, or has any ideas?

i have a dell laptop with 2GB of RAM
im using the ati flgrx driver from restricted repositories.

---

### Post by finer recliner on 2007-12-03
bump

---

### Post by RebounD11 on 2007-12-03
I've had that problem, only it was with the nvidia driver. I did a modprobe nvidia and rebooted, never had the problem again since... I don't know if this fixed it or it was just a coincidence, but you could try a modprobe with whatever the ATI equivalent would be, I think fglrx but I really don't know :D

Or you could try uninstalling and reinstalling Compiz. If it doesn't work I don't know what to say...

PS: If you can't help at least say so... personally I hate the Bump...especially as first reply...

---

### Post by finer recliner on 2007-12-03
thanks for the reply, i have a question though:

any changes concerning the kernel starts to make me worry, so i'd just like to know what the command
```

modprobe nvidia

```

is supposed to do before i go searching for an ATI equivalent. also, how can i undo the command if it screws things up even more?

thanks!

---

### Post by finer recliner on 2007-12-09
never got a response  :-/

bumps

---

