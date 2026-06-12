---
title: "Restarting X Server After Changing x config file"
date: 2009-09-19
forum: Desktop Environments
---

### Post by theanti9 on 2009-09-19
I just installed ubuntu and updated the nvidia drivers for my graphics cards (I have 3 monitors and I want them all to run) so after I did that, I went to the nVidia control panel to activate my second 2 monitors. I activated them and changed the positions to where I needed them to be, and it said I need to restart X Server for my changes to take effect and that I needed to save the changes to the x server config file. So I saved the changes to the config file, went to my terminal and did:

```
sudo /etc/init.d/gdm restart
```

it takes me to a blank screen with no terminal, just a blinking cursor in the corner, and stays there for about 10 minutes. until it comes up with

```
* Reloading SYSTEM LOG DAEMON...
```

and then that just stays there forever. How do I get x server to start again. I have no terminal, just a blank black screen pretty much. What do I do?

---

### Post by theanti9 on 2009-09-19
also, for some reason, after savin the x configuration file, when i restart the computer, it goes back to the same, original configuration, and my changes aren't actually saved. so theres no way for me to actually get my monitors working

---

### Post by Conzo on 2009-09-19
> **theanti9 said:**
> also, for some reason, after savin the x configuration file, when i restart the computer, it goes back to the same, original configuration, and my changes aren't actually saved. so theres no way for me to actually get my monitors working
 
 
 
[http://ubuntuforums.org/showthread.php?t=1216691](http://ubuntuforums.org/showthread.php?t=1216691)
 
old post with the problem follow the dir.. works great 
 
 
Conzo!

---

