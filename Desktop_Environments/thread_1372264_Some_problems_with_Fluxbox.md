---
title: "Some problems with Fluxbox"
date: 2010-01-04
forum: Desktop Environments
---

### Post by Siken on 2010-01-04
Hello,
before i start to describe my 2 problems, i want to say that i am german and my english isn't so good :)
But I wanted to ask my question in the english forums, because I think here are more people active.
So, forgive me for my broken english :D


So, i got 2 main problems with fluxbox:


1) When I start fluxbox, i want that 2 apps are automatically started too => autostart.
The 2 apps are wBar and conky.
I tried a few methods for the autostart of this 2 apps:
 -to edit the ~/.fluxbox/startup file like it's described in this file :D
 -then to include a bash script with sleep in the ~/.fluxbox/startup file like i read it in a tutorial
 -and i tried to write conky in the rootcommand line in ~/.fluxbox/init ( conky & ) and to write wBar in the startup file.


But in all 3 cases, just wbar starts and not conky =(
So i can just start it manually, but i dont want to do this all the time =(


2) Everytime when I reboot my PC, my sound is set to silent, i can just change it with gmix =(

Hope you understand what I mean an you can help me with my problems :D 

MfG
Siken

---

### Post by BluesRunTheGame on 2010-01-08
I think this addresses your second problem: [http://ubuntuforums.org/showthread.php?t=878170](http://ubuntuforums.org/showthread.php?t=878170)

---

### Post by HandyAndy on 2010-01-10
I have conky to start with fluxbox.

I simply added *conky &* in my *~/.fluxbox/startup file* in the section that starts "# Applications you want to run with fluxbox" and before "#And last but not least we start fluxbox".

I don't know anything about wBar, I'm afraid.

I have the same issue with the sound starting muted. I haven't got an answer, but I have a work around. I put *gnome-volume-control-applet &* in my startup (as above). That at least gives me the volume control in my taskbar so that I can quickly and easily turn the sound back on.

I hope some of this helps :)

---

### Post by tweaksource on 2010-01-22
add wbar and conky to startup.

You must use 

wbar &

conky &

If you don't have the '&' then the next app won't start.

---

