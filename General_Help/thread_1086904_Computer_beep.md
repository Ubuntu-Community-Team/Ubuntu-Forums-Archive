---
title: "Computer beep"
date: 2009-03-04
forum: General Help
---

### Post by joshaman on 2009-03-04
is there a way to stop ubuntu from using my internal pc beep speaker beside turning it off from BIOS?

---

### Post by anubhavrocks on 2009-03-04
see if this works:
 ```
sudo modprobe -r pcspkr
```

---

### Post by HermanAB on 2009-03-04
You could just unplug the speaker or snip the wire too!

H.

---

### Post by joshaman on 2009-03-04
> **anubhavrocks said:**
> see if this works:
 ```
sudo modprobe -r pcspkr
```

thanks!

---

### Post by bungleman on 2009-05-25
just a quick bit of additional information,

I read in another thread a way to run the command at boot:

gksudo gedit /etc/crontab

add:

@reboot root modprobe -r pcspkr

---

### Post by sedawk on 2009-05-25
Have you tried
```

xset -b off

```

or 

```

setterm -bfreq 0

```

In the Gnome Control Center there is an Option "Sound". One Tab is "System Beep" where you can
also turn it off!

---

