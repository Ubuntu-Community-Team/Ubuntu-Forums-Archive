---
title: "Resume with autologin"
date: 2007-06-02
forum: Desktop Environments
---

### Post by Vies1 on 2007-06-02
Hi everyone,

I'm building a Mythtv-frontend over Ubuntu Feisty and running in to some nasty problems. Well actually just one problem. 

I have set autologin trough gdm and everything is working like a charm. I have suspend-to-ram working so that I can start frontend quickly. Problem is, that autologin after the resume works only first time, right after the initial boot. After that, I have to enter password to login.

Is there way to disable that login after resume completely , or just work around it with some resume script or something

Vies

---

### Post by teachop on 2007-06-03
Have you tried working with the settings in Configuration Editor?  Under System Tools-> Configuration Editor -> apps-> gnome-power-manager is a setting called "lock_on_suspend" that is checked by default.

If you don't see Configuration Editor in the Main Menu, right click on the Main Menu and pick Edit.

---

### Post by Vies1 on 2007-06-03
Ok, found it, thanks.

But now I have another problem. Concerning lirc and mythtv. When I resume from suspend, remote is not working. It seems that the problem is not the lirc, but mythtv loses lirc some how. If I exit mythfrontend and restart it, everything works like charm again.

I tried to kill mythfrontend before suspending, but somehow I was unable to start it automatically using script located in resume.d folder

I made following 97-myth-start.sh script, made it executable, but seems that it doesn't work

```
#!/bin/bash

sudo /usr/bin/mythfrontend
```

I have set that my user can execute mythfrontend using sudo without password, so that shouldn't be the problem.

Any idea howto get myth realize lirc after suspend or some way to start it automatically using resume script

Vies

---

### Post by Vies1 on 2007-06-19
Hi everyone,

Still having above problem, any ideas?

---

