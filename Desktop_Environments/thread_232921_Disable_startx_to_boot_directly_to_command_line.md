---
title: "Disable startx to boot directly to command line?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Buell on 2006-08-09
How can I prevent startx from running so I can boot directly to the command line? Is there a file I can edit to temporarily prevent the xserver from starting during boot?

Thanks

---

### Post by zxee on 2006-08-09
Edit /etc/inittab 
Make the default runlevel 1 (normally in ubuntu set to 2)
That should do it.

---

### Post by etank on 2006-08-09
Someone correct me if I am wrong but in Ubuntu runleves 2-5 are all the same. Edit /etc/inittab and at the top you will see a line like 
```
# The default runlevel.
id:2:initdefault:
``` change that to say```
# The default runlevel.
id:3:initdefault:
```then run```
sudo rm /etc/rc3.d/S13gdm
```That way you can still run ```
startx
```to get to the gui and if you want to go back to the gui by default then you just need to chage the 3 to a 2 in /etc/inittab. I hope that helps.

---

### Post by zxee on 2006-08-09
Ok maybe I'm wrong. I thought ubuntu uses runlevels 1 & 2.
If you do init 3 in a terminal it doesn't kill the xserver.

---

### Post by etank on 2006-08-09
I think that runleve 1 is single user mode. 2 - 5 are all the same and are multiuser. I think that is right at least.

---

### Post by redbull_monsta on 2006-08-09
thats strange - normal runlevel on gui linux is 5, shell is 3 not sure why it is 2 on ubuntu.....

---

### Post by etank on 2006-08-09
I thought the same thing when I first started using Ubuntu as well.

---

### Post by bensexson on 2006-08-09
Wouldn't the easist way be to just use Recovery Mode?

---

### Post by Ramses de Norre on 2006-08-09
Recovery mode gives you a root only environment, no good idea!
The easiest and safest way is installing sysv-rc-conf (sudo aptitude install sysv-rc-conf) and using it (sudo sysv-rc-conf) to remove gdm from runlevel 2 (delete the X there).
By using sysv-rc-conf you can easily reverse your changes later.

---

### Post by etank on 2006-08-09
Good call. I had not seen sysv-rc-conf before.

---

