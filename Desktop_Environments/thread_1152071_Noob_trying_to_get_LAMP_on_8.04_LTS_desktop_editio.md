---
title: "Noob trying to get LAMP on 8.04 LTS desktop edition"
date: 2009-05-07
forum: Desktop Environments
---

### Post by cvl1983 on 2009-05-07
Hi Everybody,

I am a Ubuntu noob (but I know and understand everything about Windows, and been a web developer / PHP programmer for many years). 

Just bought a new server a few weeks ago, and have been stumped... I installed Linux desktop edition (8.04 LTS from Ubuntu website), got it all up and running. I tried to install new programs such as mysql-client, mysql-server, php5, php5-mysql, php5-mysqlite, mysqlite3, apache2, to establish a LAMP server with a GUI desktop.

NOTE: I do not have an etrhernet connection yet on this machine...Please let me know if it requires it, or if the CD is fine...

Problems: tried installing Server Edition first, and had trouble getting Gnome installed, so I then installed the desktop edition to hopefully have a GUI, and install LAMP onto it.

So, both methods have me stumped. Either I cannot connect to get new software, or I am doing something wrong...
Please help!

By The Way: here's my hardware...

HP Proliant Dual Xeon 3.06MHZ 3GB RAM, 2x36GB U320 HDD
Linux 8.04 LTS Desktop edition
stock installed programs, no extras at this time

---

### Post by Headbanger2510 on 2009-05-07
You should install first the SE of ubuntu, then connect to the internet and if you whish to have a gui, you should install ubuntu-desktop by doing:
sudo apt-get install ubuntu-desktop

---

### Post by mcduck on 2009-05-07
I recommend first getting the internet connection to work on that machine. That will make your life a *lot* easier.

After that installing LAMP on desktop version of Ubuntu is very simple. Running following command does it all for you:
```
sudo tasksel install lamp-server
```

On th other hand, if you decide to install the server version instead you can insatll desktop on it with this command:
```
sudo apt-get install ubuntu-desktop
```

..but since you already have the desktop version on the machine, and I assume you are going to use it for desktop tasks as well I recommend just staying with the Desktop version you have. You will not need the kernel optimized for server use, and as Ubuntu beginner you will most likely have easier time working with a graphical desktop from the beginning (the server version only has a command-line interface by default).

---

### Post by cvl1983 on 2009-05-07
Thanks guys...I will focus on getting connected and work from there. Thanks. I will post an update to follow up on the progress.

---

