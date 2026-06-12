---
title: "UbUnTU: sound problems/ pain in the ***"
date: 2009-04-27
forum: General Help
---

### Post by erdal123 on 2009-04-27
i now have this soundproblem over 2 months i virtually tried everything on the internet but no success

its very sad because its the only thing that holds me stepping over to linux OS
and that includes: pulseaudio fix, alsa fix and other fixes which are confusing 

i have a creative X-fi xtreme card, does anyone have a fix for this 

thanks

---

### Post by Nepherte on 2009-04-27
Try this: [http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

---

### Post by erdal123 on 2009-04-27
> **Nepherte said:**
> Try this: [http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

i get this warning :

windozz@ubuntu:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.save line 1: ignoring bad line starting with 'grep'
WARNING: /etc/modprobe.d/alsa-base.save line 3: ignoring bad line starting with 'x'

---

### Post by erdal123 on 2009-04-27
i get this warning :(

---

### Post by erdal123 on 2009-04-27
> **erdal123 said:**
> i get this warning :(

any TIPS?

---

### Post by Nepherte on 2009-04-28
Hmm warnings may generally be ignored. But I guess it's still not working for you. Can you post the content of that file?
```
cat /etc/modprobe.d/alsa-base.save
```

---

### Post by erdal123 on 2009-04-28
> **Nepherte said:**
> Hmm warnings may generally be ignored. But I guess it's still not working for you. Can you post the content of that file?
```
cat /etc/modprobe.d/alsa-base.save
```

how do you open a .sav file? sry

---

### Post by erdal123 on 2009-04-29
> **erdal123 said:**
> how do you open a .sav file? sry

any help?

---

### Post by Nepherte on 2009-04-30
Just run the command:
```
cat /etc/modprobe.d/alsa-base.save
```
in a terminal (Alt+F2 and type gnome-terminal to open up a terminal).

---

### Post by erdal123 on 2009-04-30
> **Nepherte said:**
> Just run the command:
```
cat /etc/modprobe.d/alsa-base.save
```
in a terminal (Alt+F2 and type gnome-terminal to open up a terminal).

cat /etc/modprobe.d/alsa-base.save

outcome:

cat: /etc/modprobe.d/alsa-base.save: Permission denied

---

### Post by Nepherte on 2009-05-01
try
```
sudo cat /etc/modprobe.d/alsa-base.save
```

---

### Post by erdal123 on 2009-05-01
> **Nepherte said:**
> try
```
sudo cat /etc/modprobe.d/alsa-base.save
```

outcome:

grep 'audio' /etc/group

x

---

### Post by Nepherte on 2009-05-03
Well you can definetely say that it doesn't belong there. You can safely remove:
```
grep 'audio' /etc/group
```
It's not really clear to me, do you have sound? The warning says it has detected it as a bad line and ignored it. So as far as your initial post goes, the install was successful and you have sound.

---

