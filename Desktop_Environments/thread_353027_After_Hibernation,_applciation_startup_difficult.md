---
title: "After Hibernation, applciation startup difficult"
date: 2007-02-04
forum: Desktop Environments
---

### Post by Thomas Rasmussen on 2007-02-04
Hey

I'm running a fully updated Ubuntu 6.10 and using Gnome as my desktop environment. I have some problems when my computer resumes from hibernation, then I usually have difficulties with starting applications (xterm, firefox, gnome-terminal etc). If I happen to have a terminal open or switch to text-mode, then I can delete the file in /tmp/.ICE-unix and apps start, but usually delayed a couple of seconds.

If launching an app from the terminal, it will display the following message:
**Warning: Tried to connect to session manager: Could not open network socket**

I know that it is probably related to the .ICE-unix directory, but what can I do to avoid this? If I logout of gnome and restart X (well, actually restarting GDM) then it all works perfectly until my next hibernation, and as I usually use hibernation instead of complete shutdown, this is rather annoying.

Regards
Thomas

---

### Post by flossgeek on 2007-02-04
hibernate and suspend are hit and miss, they dont work on many machines im afraid.

---

### Post by Thomas Rasmussen on 2007-02-04
Well, the actual hibernate works perfectly on my machine, it powers off and resumes when power button is pushed, but it appears as though gnome doesn't fully understand what to do when it is resumed. 

My guess is that there is something missing in the resume script that needs to be performed, but I'm not entirely sure what this might be.

---

### Post by aferrandi on 2007-02-07
Same problem for me, using an Acer 1400.
But I was never able to launch the applications from terminal, since it does not start ;-)  .
How do you do it?

What I normally do is to press Ctrl-Alt-Backspace to restart Gnome. After that everything works fine.

---

### Post by aferrandi on 2007-02-08
It looks that this problem is covered by [bug #49221]("https://launchpad.net/ubuntu/+source/gnome-session/+bug/49221")

---

