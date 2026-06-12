---
title: "Can not connect to 16.04.1 desktop using vnc"
date: 2016-12-01
forum: Desktop Environments
---

### Post by mclovis on 2016-12-01
Hi, 

I have an number of computers at home running Ubuntu 16.04 and am able to connect to all but one. I have enabled remote desktop and switched encryption setting using dconf. I can use VNC and connect to the same machine using non-localhost address and ssh into machine. However when I try to connect from windows using tightvnc (which is the viewer I use for other machines), I receive no message and yet can see that it is still running as a process. Tested connecting to other machines also, I get prompt and all is well. I am going to tee a log file for vnc server to try to understand. I disabled firewalls, and ip routes fine. Any other ideas?

Thanks in advance,
Mike

---

### Post by zapp2 on 2016-12-01
Have you tried this website: [https://knowledgelayer.softlayer.com/learning/tightvnc-server-ubuntu-1604](https://knowledgelayer.softlayer.com/learning/tightvnc-server-ubuntu-1604)  
I have tightvnc also at home and it works perfectly on all my PC´s. I use this website as number one solution page.

---

### Post by mclovis on 2016-12-01
Ok, finally answered it (or found a solution). Removed tightvncserver. Ignored default server, as it was not starting all of the time. Set server defaults (for good luck) shown here [http://ubuntuhandbook.org/index.php/2016/07/remote-access-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/07/remote-access-ubuntu-16-04/). Installed x11vnc server as shown here [http://tqdev.com/2016-install-vnc-on-your-ubuntu-16-04](http://tqdev.com/2016-install-vnc-on-your-ubuntu-16-04). Used command to set password for /path/to/pw-file as such : sudo x11vnc -storepasswd SomeVerySecurePassword /etc/x11vnc.pass. Changed upstart file to reflect what was going on: 

exec /usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /tmp/x11vnc.log -usepw

rebooted to make sure (could use killall command also). Hope this helps others.

---

