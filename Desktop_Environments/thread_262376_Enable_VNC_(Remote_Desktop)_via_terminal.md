---
title: "Enable VNC (Remote Desktop) via terminal"
date: 2006-09-21
forum: Desktop Environments
---

### Post by midspot on 2006-09-21
How do I enable Remote Desktop in Drake via the command line (terminal)

I cannot seem to find the config file to turn it on and control the options.

thanks

---

### Post by lamego on 2006-09-21
You will need to install a vnc server package, the config should me somewhere on /etc .

---

### Post by midspot on 2006-09-21
I mean when you go to the System menu then Preferences then Remote Desktop and turn on the settings there. How do I do that via the command line?

thanks

---

### Post by hellmet on 2006-10-12
same doubt here...

---

### Post by xdefconx on 2008-01-25
I also looking for this solution. How via terminal we can enable remote desktop? thanxs

---

### Post by reader4 on 2008-01-30
SSH to the machine and 

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```

---

### Post by bobyy on 2008-02-02
> gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

THX reader4...you save me.....in a desperate situation..thx again

---

