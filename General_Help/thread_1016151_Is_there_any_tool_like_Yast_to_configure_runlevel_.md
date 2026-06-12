---
title: "Is there any tool like Yast to configure runlevel service?"
date: 2008-12-19
forum: General Help
---

### Post by anantgowerdhan on 2008-12-19
Hi,

I've used openSuse and I'm very much comfortable with Yast. the only problem now I have is with KDE4.1 and I thought to look another options. I found Ubuntu is a great replacement for openSuse but I dont see any runlevel service configuration tool to start stop services. 

Please let me know if any such tool is available in ubuntu.


Regards,
Ananrt

---

### Post by bodhi.zazen on 2008-12-19
With KDE you will need to look in the menu (On gnome it is under System -> services).

Not exactly the same as YAST mind you as YAST is kind of like one - stop - shopping ...

Otherwise use the command line, update-rc.d

---

### Post by scorp123 on 2008-12-19
> **anantgowerdhan said:**
> but I dont see any runlevel service configuration tool to start stop services. per default there are no services running and therefore there is no such GUI tool there per default (the command line has the "update-rc.d" command though which is similar to OpenSUSE's "insserv" command ...). The logic here seems to be that if you installed Ubuntu Desktop you're not running a server and you don't need such a tool and if you installed Ubuntu Server which doesn't have any GUI (yes, text only!) then you're a pro and can live without such a tool as well ....  Or something like that.

So you will have to install such a tool from the repository. My suggestion would be this one: **bum** ... which is short for "BootUp Manager". To install it from the terminal: ```
sudo apt-get install bum
```

Or in "Synaptic": Search for the package with the name "bum" and install it.

Once it's installed you will find it in the top panel menu:
[INDENT]System > Administration > Boot-Up Manager[/INDENT]

Screenshot:
[IMG]http://www.marzocca.net/Immagini/bum1_th.png[/IMG]

Full size version:
[http://www.marzocca.net/Immagini/bum1.png](http://www.marzocca.net/Immagini/bum1.png)

BUM's homepage is here:
[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by scorp123 on 2008-12-19
Oh, and please keep this in mind:

Debian-like distros such as Ubuntu do **_everything in Runlevel 2_** whereas OpenSUSE uses a more classic approach with various runlevels doing various things (e.g. Networked + No GUI: Runlevel 3, Networked + GUI: Runlevel 5, etc.)

So in "bum" it's enough if you enable or disable a service, there is no need to assign it to a particular runlevel ...

---

### Post by anantgowerdhan on 2008-12-19
Hi Scorp,

See why I'm looking for this tool is because I want to start stop VMWare server, MySQL and Tomcat as per my choice. I felt its better in YAST. What you are suggesting (BUM) is seems like configuring the boot time services.

Let me know if BUM can do such things.

Regards,
Anant

---

### Post by scorp123 on 2008-12-19
> **anantgowerdhan said:**
> See why I'm looking for this tool is because I want to start stop VMWare server, MySQL and Tomcat as per my choice. In that case, wouldn't it be easier and faster to simply create a launcher icon which does precisely that? Let's take VMware Server as example: the shell command to get the service started is something like:
```
gksudo /etc/init.d/vmware-server start
```

Create a custom icon on your desktop (right-click on Desktop > Create Launcher > ....) and put the line above into the part where it says "Command: .... "

Voila, done. One click, one password, and VMware Server starts.

You used Yast to do this? That's a bit overkill. ;)

---

### Post by oldos2er on 2008-12-19
Use sysv-rc-conf.

---

### Post by bhy on 2011-03-01
> **scorp123 said:**
> In that case, wouldn't it be easier and faster to simply create a launcher icon which does precisely that? Let's take VMware Server as example: the shell command to get the service started is something like:
```
gksudo /etc/init.d/vmware-server start
```

Create a custom icon on your desktop (right-click on Desktop > Create Launcher > ....) and put the line above into the part where it says "Command: .... "

Voila, done. One click, one password, and VMware Server starts.

You used Yast to do this? That's a bit overkill. ;)

well, one could say that the launcher creation scenario is a bigger overkill:)

---

