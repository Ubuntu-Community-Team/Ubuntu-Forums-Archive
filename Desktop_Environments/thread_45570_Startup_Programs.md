---
title: "Startup Programs"
date: 2005-06-30
forum: Desktop Environments
---

### Post by karmah on 2005-06-30
I'm not sure if this is the right subforum...but wth.
My problem this time is that like 20 programs start up when I boot (like 7, but three of each.) And I've checked Settings>Session>startup programs, ad it was empty. I used to have "Automatically save current setup" activated, but i deactivated it some time ago because of this problem. But it didn't stop and I can't find why my programs have turned against me :(, This sucks up all my ram and is just mainly annoying, all help highly apreciated.
thx in advance.

---

### Post by Xian on 2005-06-30
[QUOTE=karmah]I'm not sure if this is the right subforum...but wth.
My problem this time is that like 20 programs start up when I boot (like 7, but three of each.) And I've checked Settings>Session>startup programs, ad it was empty. I used to have "Automatically save current setup" activated, but i deactivated it some time ago because of this problem. But it didn't stop and I can't find why my programs have turned against me :(, This sucks up all my ram and is just mainly annoying, all help highly apreciated.
thx in advance.[/QUOTE]
What I would suggest is that while you are in a Gnome session and have all these programs running, that you go about closing all of them, _and then_ when you log out tick the box that says 'Save Current Setup'. Next, log back in.

---

### Post by karmah on 2005-07-01
Yay! it's working! thx alot :)

---

### Post by FLeiXiuS on 2005-07-01
Or, if you really want to get customized, you can remove programs from loading in a specific runlevel.  /etc/rc*.d/

Simple replace the * with the run level you'd like to modify.

$ cd /etc/rc*.d/
$ ls

Now remove executable permissions to those which you don't want to load.  

$ chmod -x 

Now for an example, I don't use mdadm raid soo why should that service be running?

$ cd /etc/rc2.d/
$ sudo chmod -x *mdadm*
Note: The asterisks here are wildcards.

That should do it, next time you enter that runlevel it will never load again.  Also just a reminder, not every runlevel is used.  So more then one runlevel will have certain scripts loading.  For instance, runlevel 1 has mdadm-raid.  But you've disabled mdadm in runlevel 2.  In order to get to runlevel 2 you have to go through 1.  So in other words, you have to disable mdadm in runlevel 1 and 0 also.

Removing from runlevel 0
$ cd /etc/rc0.d/
$ sudo chmod -x *mdadm*
Removing from runlevel 1
$ cd ../rc1.d/
$ sudo chmod -x *mdadm*


Just an extra 2 cents :-P  enjoy!

---

