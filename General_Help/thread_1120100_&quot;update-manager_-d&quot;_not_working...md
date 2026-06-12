---
title: "&quot;update-manager -d&quot; not working.."
date: 2009-04-08
forum: General Help
---

### Post by aktiwers on 2009-04-08
```
update-manager -d
```Is not working when I run it from ALT+F2..  notrhing happends.. 

I just rebooted and tried again, but still nothing?

When I run the command in terminal it says:
```

aktiwers@HAL2:~$ update-manager -d
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk
aktiwers@HAL2:~$ 


```Whats going on?

---

### Post by SuperSonic4 on 2009-04-08
Have you tried running the command as root?

---

### Post by aktiwers on 2009-04-08
Thanks for the reply.
Same thing..  

But it seams like I am missing pygtk, though I can't find it in Synaptic?

---

### Post by rafemonkey on 2009-04-08
Sounds like update-manager has lost some of it's dependencies, try the following from a command line: ```
sudo aptitude reinstall update-manager
```

---

### Post by aktiwers on 2009-04-08
> **rafemonkey said:**
> Sounds like update-manager has lost some of it's dependencies, try the following from a command line: ```
sudo aptitude reinstall update-manager
```

Thanks..  found that "Computer-janitor" had messed it up and removed some libs.

Thanks its working now!

---

