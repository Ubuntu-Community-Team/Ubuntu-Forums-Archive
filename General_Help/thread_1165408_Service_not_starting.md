---
title: "Service not starting"
date: 2009-05-20
forum: General Help
---

### Post by mb_webguy on 2009-05-20
I'm running the folding@home client -- or trying to.  For some reason the service isn't being started at boot.  I installed the client using the finstall script, as mentioned on the [Ubuntu documentation]("https://help.ubuntu.com/community/FoldingAtHome").  I ran the installService script to copy the folding script to the /etc/init.d directory and update the rc links.

update-rc.d threw an error about the folding script not having the proper info, so I added the following standard init info block at the beginning of the script, just after the shebang.```
### BEGIN INIT INFO
# Provides:          folding
# Required-Start:
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: F@H client
# Description:       This file starts the folding@home client
### END INIT INFO
```

I have verified that the folding script is located in the /etc/init.d directory, and the proper links were added to the various runlevel script directories:```
matt@the-tardis:~$ sudo find /etc -name *folding
/etc/rc1.d/K20folding
/etc/rc4.d/S20folding
/etc/rc6.d/K20folding
/etc/rc2.d/S20folding
/etc/init.d/folding
/etc/rc5.d/S20folding
/etc/rc3.d/S20folding
/etc/rc0.d/K20folding
```As you can see, the service should be started on runlevels 2, 3, 4, and 5, and stopped on 0, 1, and 6.  The problem is that it isn't.  When I reboot and check "top" in the terminal, the processes aren't listed, and should I try to stop the service with "sudo /etc/init.d/folding stop", the service is reported as not running.  However, I can start it manually using "sudo /etc/init.d/folding start" with no problems.

I tried manually removing and adding the service rather than using the installService script...```
matt@the-tardis:~$ sudo rm /etc/init.d/folding
matt@the-tardis:~$ sudo update-rc.d -f folding remove
 Removing any system startup links for /etc/init.d/folding ...
   /etc/rc0.d/K20folding
   /etc/rc1.d/K20folding
   /etc/rc2.d/S20folding
   /etc/rc3.d/S20folding
   /etc/rc4.d/S20folding
   /etc/rc5.d/S20folding
   /etc/rc6.d/K20folding
matt@the-tardis:~$ sudo cp ~/foldingathome/folding /etc/init.d/
matt@the-tardis:~$ sudo update-rc.d -f folding defaults 99
 Adding system startup for /etc/init.d/folding ...
   /etc/rc0.d/K99folding -> ../init.d/folding
   /etc/rc1.d/K99folding -> ../init.d/folding
   /etc/rc6.d/K99folding -> ../init.d/folding
   /etc/rc2.d/S99folding -> ../init.d/folding
   /etc/rc3.d/S99folding -> ../init.d/folding
   /etc/rc4.d/S99folding -> ../init.d/folding
   /etc/rc5.d/S99folding -> ../init.d/folding
```... but it makes no difference.  As you can see, after a reboot the service still isn't starting, but I can start it manually.```
matt@the-tardis:~$ sudo /etc/init.d/folding stop
[sudo] password for matt: 

['folding' ver. 6.2]

Stopping of FAH client(s):
Phase #1
No FAH clients are running...
No FAH cores are running...

Stopping of FAH client(s): OK 
matt@the-tardis:~$ sudo /etc/init.d/folding start

['folding' ver. 6.2]

Starting up FAH client(s) on 2 processor(s):
Starting FAH client at CPU1...
FAH client #1 startup: OK 
Starting FAH client at CPU2...
FAH client #2 startup: OK 


Starting of FAH client(s): OK
```And yes, I've tried this both with and without the init info block I mentioned I added to the folding script, to make sure that's not somehow the cause.  

I've been using *nix systems for over 10 years now, and never had this kind of problem with a service.  Any ideas?

---

