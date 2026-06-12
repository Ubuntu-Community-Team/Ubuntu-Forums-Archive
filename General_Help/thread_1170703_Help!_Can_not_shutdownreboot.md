---
title: "Help! Can not shutdown/reboot"
date: 2009-05-26
forum: General Help
---

### Post by mzhb@mac.com on 2009-05-26
I am new to ubuntu and today I installed ubuntu 9.0.4 on my laptop.
The laptop is samsung r25. 

Everything works very well. But I have a problem of shutting down my machine. 
Whenever I choose to shut down or reboot, screen will change to some wired image (just like your video card stops working) and system freeze forever. 

I tried to use command line to shut down the system and no luck either...

Is something wrong with my video card (ATI Radeon)? Or anyway I can check the log info during system shutdown. 

Thanks in advance!!

---

### Post by mzhb@mac.com on 2009-05-26
Anyone experienced the same problem before??

---

### Post by Nareto on 2009-05-26
hello, as a temporary workaround for shutting down you can switch to a console with the key combination
```
Ctrl + Alt + F1
```
there login with your username and password, and then type
```
sudo shutdown -h now
```
this should do it properly.

For a more proper solution, i would start finding out what driver you have installed for your graphics card (sorry, i wouldn't know how to do that) - sometimes propietary drivers work better.

---

### Post by hac13 on 2009-05-26
This thread might help: [http://ubuntuforums.org/showthread.php?t=294839&highlight=edgy+logout](http://ubuntuforums.org/showthread.php?t=294839&highlight=edgy+logout)

The suggested solution is to first open the GDM config file by typing this in a terminal:

```
sudo gedit /etc/gdm/gdm.conf-custom
```

And to then add this text after [daemon]:

```
AlwaysRestartServer=true
```

---

