---
title: "My computer became very slow"
date: 2007-05-30
forum: Desktop Environments
---

### Post by bosshoof on 2007-05-30
Hi
i have  
CPU: intel 3.0GHz
RAM: 256 MB
Main board: Gigabyte 915GM  with built in graphics card

trying to reconfigure  my x-server to choose  a driver , i wrote
```
 sudo dpkg-reconfigure xserver-xorg 
```

i didn't find a driver called intel or something alike
but i choose the i810 driver   
and continued and rebooted my PC
but when i logged in 
the PC was  very slow ant it hangs when i open the terminal
i don't know why ????!
plz tell me what to do

---

### Post by kevinlyfellow on 2007-05-30
Intel graphics should work by default without user configuration.  Try this

```
sudo dpkg-reconfigure xserver-xorg -pcritical
```

---

### Post by bosshoof on 2007-05-30
i tried it but  no chage <or a slight change >
plz look at the attached pictures
and tell if there is something wrong?

---

### Post by kevinlyfellow on 2007-05-30
Everything looks ok, I guess.  Its tough to be able to say what will and won't work on your hardware (thats why its all automated now ;-)).  i810 is the proper driver.  How much memory does the graphics card have?  

What you can do is look for backups of your original xorg.conf (always back up xorg.conf before you do anything to it!).  They can be found in /etc/X11/

You could boot the live cd for Ubuntu and copy the xorg.conf from that.  

I'm not convinced that its an xorg problem, but since you said it happened after you tried to reconfigure, I tend to believe it.  You didn't do anything else did you?

Edit: post a copy of your xorg.conf if you still can't get it working.  That will tell me much more than the pictures you posted

---

### Post by FuturePilot on 2007-05-30
You could also do ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
That will return it to the default configuration with minimal input from you. Much easier than manually doing it.

---

