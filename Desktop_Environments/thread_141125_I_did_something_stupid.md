---
title: "I did something stupid"
date: 2006-03-07
forum: Desktop Environments
---

### Post by xhie on 2006-03-07
Yeah so...

While trying to figure out how to map some of the toshiba keys on my R15 to do stuff I messed around with my xinitrc file, I added 2 lines to it, restarted X and the stuff I did didn't work. 

Ok, I think to myself, whatever, I'll go back to trying to figure it out later, while doing other stuff I had to run gedit as sudo, it askes for my password, I type it in, it dosent work... I try to just run as root, su, it askes for the password and dosent work. Says Authorization failed. 

I decided to undo the stuff I did the the xinitrc file, I boot into recovery mode, give it the root password, which it takes happily and change the xinitrc file back to what it was before I started messing with it. 

Reboot, log in, try to do something as sudo, then as root in the terminal and it dosnet work. 

What did I mess up and how do I fix it?

I know i'm probably being stupid here, but I'm really at a loss as to what to do next.

---

### Post by codejunkie on 2006-03-07
[QUOTE=xhie]Yeah so...

While trying to figure out how to map some of the toshiba keys on my R15 to do stuff I messed around with my xinitrc file, I added 2 lines to it, restarted X and the stuff I did didn't work. 

Ok, I think to myself, whatever, I'll go back to trying to figure it out later, while doing other stuff I had to run gedit as sudo, it askes for my password, I type it in, it dosent work... I try to just run as root, su, it askes for the password and dosent work. Says Authorization failed. 

I decided to undo the stuff I did the the xinitrc file, I boot into recovery mode, give it the root password, which it takes happily and change the xinitrc file back to what it was before I started messing with it. 

Reboot, log in, try to do something as sudo, then as root in the terminal and it dosnet work. 

What did I mess up and how do I fix it?

I know i'm probably being stupid here, but I'm really at a loss as to what to do next.[/QUOTE]
you most likely changed the permissions of the xinitrc file to change it back to the default values run 
```
sudo chown root:root /etc/X11/xinit/xinitrc
```
then
```
sudo chmod 644 /etc/X11/xinit/xinitrc
```
and try logging back in.

---

### Post by xhie on 2006-03-07
dunno how I managed that...

Thanks :)

---

