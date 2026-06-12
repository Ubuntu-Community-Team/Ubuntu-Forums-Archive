---
title: "Getting ifupdown to cooperate with Network Manager"
date: 2012-06-08
forum: Desktop Environments
---

### Post by jcllings on 2012-06-08
You wind up with this deal where network-manager doesn't start when eth0 doesn't connect, i.e. when you are 'a goin mo-bile (i.e. wireless). It's irritating.  So I wrote this script: 

 #!/bin/bash

 ifconfig eth0 | grep inet 

 if [[ $? != 0 ]];then 
 	service network-manager stop
 	service network-manager start
 fi

...and called it networkManagerFix.sh.  I put it in /opt/scripts where I put all my scripts and where my backup system is configured to look when it does a backup. Put a link to this script in /etc/init.d/ 

sudo ln -s /opt/scripts/networkManagerFix.sh /etc/init.d/networkManagerFix

Then I added it to Ubuntu's startup scripts: 

sudo update-rc.d networkManagerFix defaults

Then as an afterthought I fired up bum (Boot-Up Manager), selected the "Advanced" check box at the bottom and then the "Services" tab, scrolled to and right clicked and changed it's startup priority to 99. This seems to have done the trick. Now even if my ethernet cable is disconnected, I get a working applet in my tray and everything is hunky dory.

---

### Post by jcllings on 2012-06-08
I tried just changing network-manager's priority just now to 99 and then disabled my fix to see if this would be sufficient. Turns out that you still wind up with no network manager.

---

