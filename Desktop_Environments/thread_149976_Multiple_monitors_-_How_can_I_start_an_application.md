---
title: "Multiple monitors - How can I start an application on secondary screen?"
date: 2006-03-25
forum: Desktop Environments
---

### Post by speedsix on 2006-03-25
Is there anyway to do this? At the moment all apps started via the terminal start on the default screen.

Basically I want an app to start on boot on my secondary monitor?


Many thanks

---

### Post by skylark on 2006-03-25
I believe launching it via:
<programname> -display :0.1

eg: xterm -display :0.1

This should also work: DISPLAY=":0.1" <programname>

---

### Post by lorre on 2006-12-11
This doesn't work for me, I am using nvidia twinview and have only 1 screen definition in my xorg.conf. Is it possible with twinview to target an application to my secondary screen?

---

### Post by orb9220 on 2006-12-11
Yes this is been ongoing problem. Gnome says it is the job of the app to  keep track and apps say it is the window manger's job. 

There is a program called devil's pie? that does what you need.
[http://www.ubuntuforums.org/showthread.php?t=75749](http://www.ubuntuforums.org/showthread.php?t=75749)

---

### Post by lorre on 2006-12-12
Thanks for your answer. In the past I have used devil's pie to startup applications on different *workspaces*, are you sure I can use devil's pie to target to different *screens* (I have 4 dual-monitor workspaces)?

---

