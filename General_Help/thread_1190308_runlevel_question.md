---
title: "runlevel question"
date: 2009-06-17
forum: General Help
---

### Post by cazz on 2009-06-17
Hi

I was thinking about maybe run my script (use it to control partimage) as a service so it run one time after the Xubuntu have start.

I have found out that I have to write

```
sudo update-rc.d backup.sh defaults 
```

to install it as a service but when I restart Xubuntu I get some strange problem.

the partimage start but show very strange and can't press OK or anything else and strange letter show.

I guess that have to be that partimage run before something important have start. so I have to maybe add my file on a diffrent level.

So my question is, what level are I going to use and how does I add my script to that level.

Or I maybe have to use "upstart" that I have read that ubuntu have but have not understand everyting yet.

I have try to add my script in rc.local but my Xubuntu dont like it at all.

I just like to run my script one time as administrator when the Xubuntu start.

---

### Post by bodhi.zazen on 2009-06-17
There are several ways to run your script.

May I ask, is the script working ? If not , fix your script first.

Then, when do you want it to run ? As the machine boots ? When you log into XFCE ?

Many options here, but I think partimage needs to be running in a terminal.

So something like :

```
xterm -e partimage
```

as you log into xfce ?

---

### Post by cazz on 2009-06-18
Hi, thanks for you replay

the script work nice, I can run i manual without any problem.

I have to run the script at administrator and I dont want to login

I want to run it when the linux load.

it is like this :)

I have a computer that both have windows and Linux install.
I like when I pick linux it going to automatic run partimage and restore the partition of the windows and then restart.

I have got everything to work, I just have to make my script work automatic

---

### Post by cazz on 2009-06-18
Hi
 After a little reading I have got it to work as a service BUT
It run more then one time??

It run when I start and when I shutdown.

I just want it to run at startup, nothing else

---

### Post by bodhi.zazen on 2009-06-18
Most likely because you are calling the script during the shutdown process.

As you have not posted your script or your specific configuration information it is difficult for use to guess why that would be.

---

### Post by cazz on 2009-06-18
ohh sorry. well my script is at work now and I'm at home but have have something like this

```

#!/bin/bash
partimage -b restore /dev/hda2 /home/clone/image.000 -f2 

```

---

