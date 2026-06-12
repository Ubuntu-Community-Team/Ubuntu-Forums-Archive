---
title: "Standby leads vmware's vmnet to disappear"
date: 2005-12-30
forum: General Help
---

### Post by chz on 2005-12-30
a better explanation of the problem...

my laptop (dell inspiron 700m) running breezy works almost wonderfully when thrown into standby (a few minor issues here and there, but thats for another thread). when at work i run vmware to use XP pro for Access and .net applications. now the problem i have is when i log onto my work domain with a fresh start of the laptop, i can access all the necessary networking tools i need.  when i go into standby (vmware is suspended of course, because it will not work correctly if not) and then log back in after a little while, and back into vmware...those networking resources/tools are gone. After twiddling around, i found out that the vmnet protocols are missing (when in terminal hitting ifconfig). if i reboot the laptop and back into vmware, im able to get everything again no problem

so now my question is, can there be a way to eliminate these from disappearing, or can i restart after i've been in standby? i've tried doing a "sudo /etc/init.d/networking restart" but that didnt help any. well any other ideas would be much appreciated.

---

### Post by caspian on 2007-01-30
Ok, I realize that I'm replying to a dead thread, but in case someone else happens to have this problem...

You need to reload the vmnet module. Before you can do this, you need to shut down the vmnet services.

To stop the vmnet services, download [vmware server](http://www.vmware.com/download/server/), extract the tarball, and execute (from the directory where the tarball was extracted to):
```
sudo ./vmware-server-distrib/installer/services.sh stop
```

Now, unload your vmnet module:
```
sudo rmmod vmnet
```

If this doesn't work, you might have to execute **sudo kill `pgrep vmnet`**. *WARNING:* This is probably a bad thing to do, but I wasn't able to find any way around it.

Now, reload the module:
```
sudo modprobe vmnet
```

And restart the services:
```
sudo ./vmware-server-distrib/installer/services.sh start[code]

(optional; do this if it still doesn't work) Run the networking config:
[code]vmware-config-network.pl
```

Now, when you run ifconfig, your vmnet interfaces should be up. Enjoy!

---

