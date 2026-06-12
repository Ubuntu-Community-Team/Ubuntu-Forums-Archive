---
title: "help changing screen resolution from cammand line or live cd"
date: 2009-02-18
forum: General Help
---

### Post by antmanguitar on 2009-02-18
Ok so my monitor is weird and if the screen resolution for my computer is to high the monitor will just shut off. So when i installed my Nvidea drivers and rebooted it set my screen resolution to high and my monitor just turns off. I hooked up my computer to my plasma tv and it worked just fine so i know the install is working. But when I tried to lower my resolution on the tv the tv didn't like any of the smaller resolutions and wouldn't display them so when i changed i had to shut it off manually and I don't think it saved my lower resolution. So I need some way to lower my screen resolution without having a screen. (btw I can view the live cd just fine)

---

### Post by wildman4god on 2009-02-18
try this: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by antmanguitar on 2009-02-18
ok well that was just way to much more to handle there isn't an easier way to fix it?

---

### Post by CKDewey on 2009-02-18
- Hold down <Ctrl> + <Alt> and press 'F2'
- Log in to the console (username and password)
- Run this command (you'll be asked for the password again): 

```
$ sudo dpkg-reconfigure xserver-xorg
```

- Use the GUI interface to configure the options
- Reboot (you can press the power button to shutdown)

--
Tom

---

### Post by antmanguitar on 2009-02-19
thanks that worked I still can't get my Nvidea drivers to work but at least I can use my computer now.

---

