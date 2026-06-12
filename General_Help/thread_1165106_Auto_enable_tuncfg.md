---
title: "Auto enable tuncfg?"
date: 2009-05-20
forum: General Help
---

### Post by drivecool on 2009-05-20
So here is my problem. I have hamachi installed on a machine running 9.04. Hamachi runs fine, but tuncfg wants the admin password on startup. Is there a way to auto enable this so it just works?

---

### Post by drivecool on 2009-05-20
Bump!

---

### Post by drivecool on 2009-05-21
Someone has to have a fix for this. Or at least an idea of how to do it.

---

### Post by Jungle_King on 2009-07-02
Im having the exact same problem.

I can figure out how to auto run tuncfg as root on boot. its driving me crazy!!

---

### Post by Jungle_King on 2009-07-02
ive worked it out! woop

ive modify the script thats on all the other guides:


[LIST=1]
[*]Create the start-up script for hamachi in your home directory, as shown below. Remember to change the user name "your name" *(line 5)* to your system user name in Ubuntu (or your linux distribution).  Call the script "hamachi."[INDENT] #!/bin/bash
###################################
### Start-up script for Hamachi ###
###################################
USER=your name
case "$1" in
start)
    /sbin/tuncfg
/bin/su - $sudo -c "tuncfg"
    /bin/su - $USER -c "hamachi start"
    ;;
stop)
    /bin/su - $USER -c "hamachi stop"
    ;;
restart|force-reload)
    /bin/su - $USER -c "hamachi start"
    /bin/su - $USER -c "hamachi stop"
    ;;
*)
    exit 1
    ;;
esac
 exit 0 
[/INDENT]
[*]Make the script executable:[INDENT]chmod +x hamachi
[/INDENT]
[*]Move the script to /etc/init.d/ directory:[INDENT]sudo mv hamachi /etc/init.d
[/INDENT]
[*]Finally, link the script to the appropriate run-level for booting up the system:[INDENT]sudo ln -s /etc/init.d/hamachi /etc/rc2.d/S99hamachi
[/INDENT][INDENT]sudo ln -s /etc/init.d/hamachi /etc/rc2.d/K99hamachi
[/INDENT]It seems **2** is the default level for Debian and Ubuntu. In most other distribution, it is **5**.
[*]Finally, reboot your system and Hamachi will be automatically loaded and connected to the server.
[/LIST]

---

### Post by drivecool on 2009-07-06
a buddy of mine figured it out and wrote a bash file for installing hamachi.. the gui is still a little finicky but i dont need the gui for what im doing.. we are still tweaking the bash file though..

thanks for the response.. there may be some stuff we can modify in our file based off what you posted here.. when we get a fully working bash file i will see about posting it here so people can get it running with little or no config..

thanks again..

---

