---
title: "Display not working"
date: 2010-06-26
forum: Desktop Environments
---

### Post by punsingh on 2010-06-26
Hi,
 
I am a very new user to Ubuntu. I have a Samsung N150 netbook. It came with windows XP. I had installed UNR alongside it and it was working great for the past 3 months. 
I wanted to learn GTK+ and followed the instructions in their tutorial. I downloaded their .tar.bz2 file and unzipped it. Then I opened the folder in the terminal and did make followed by make install. But the first program in the tutorial was still not compiling. So on this site: [http://library.gnome.org/devel/gtk/unstable/gtk-building.html](http://library.gnome.org/devel/gtk/unstable/gtk-building.html) I read that I should try ldconfig.
Once I did that, it was still not compiling. The Desktop was behaving funnily as no folder or directory was opening from the menu. I thought it would be ok if I restarted the computer but once I restarted, I was left with a mouse pointer on a black screen. Nothing worked except the power button on the computer. 
I rebooted and tried the Recovery Mode of Ubuntu, the command line was working fine. By that I mean I could open close directories, and run aptitude. I tried to reinstall a few packages from aptitude but it did not fix my display. 
 
Right now I am stuck with a mouse pointer on a black screen in ubuntu. If I press the printscreen button on my keyboard the pointer changes to the 'round waiting' thing for a moment and back to the pointer.
 
Please help. I am pretty sure there must be an easy fix to this.

---

### Post by ajgreeny on 2010-06-26
Having got to your black screen with the mouse pointer have you tried Ctrl+Alt+F1 to get to a normal command line, from which you could login and then use the command ```
startx
```

If you've already done this, I don't quite know where to go, I'm afraid.

---

### Post by punsingh on 2010-06-26
Hi,
 
Thanks.
I tried ctrl-alt-f1 and got the normal command line.When I entered startx, this is what I got:
> 
xauth: creating new authority file /home/puneetsingh/.Xauthority
xauth: creating new authority file /home/puneetsingh/.Xauthority
 
Fatal server error:
Server is already active for display 0 
[INDENT]If the server is no longer running, remove /tmp/.X0-lock
and start again
[/INDENT]Please consult the The X Org Foundation support
[INDENT]at [http://wiki.x.org](http://wiki.x.org)
[/INDENT]for help
 
ddxSigGiveUp: Closing log
 
Invalid MIT-MAGIC-COOKIE-1 keygiving up
 
xinit: Resource temporarily unavailable (errno 11): unable to connect to X server
xinit: No such progress (errno 3): Server error 

 
Please help. I do not know what to do now.

---

