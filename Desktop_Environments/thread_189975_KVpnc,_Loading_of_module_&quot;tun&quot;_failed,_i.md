---
title: "KVpnc, Loading of module &quot;tun&quot; failed, ideas?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by rjervis on 2006-06-05
Hi all,

I have just done a fresh install of Dapper and am working on migrating my VPN tunnel from an XP system to the Dapper box.  (Nearly XP Free! Two PC's Down, One to go... This VPN One :-) )

I have installed and configured Dapper fresh from the CD, I have installed all the updates using the package manager, Its a clean system and I have made no customisations as yet.  

I wanted to install the Cisco VPN Client but having read up on the web have opted for KVpnc.  I installed it using the package manager and it went in a treat, setup the profile and tried to connect.  

I get the error message "**Loading of module "tun" failed**", when I try to connect.  Having looked up this error I could find very little other that to upgrade the kernal.  (Well its a clean dapper install... and the post surgesting it was a fair bit older than dapper!)

I have checked /var/log/messages and there are no errors.  

Any Ideas?  I would really love to kill off the need for the Windows VPN Client.

---

### Post by DarkStarDeity on 2006-06-07
I had the same problem, I found the solution [here]("http://doc.gwos.org/index.php/VNC_and_Hamachi") (same as [this thread]("http://www.ubuntuforums.org/showthread.php?t=135036") here on the forums) -

sudo modprobe tun

then open your /etc/modules file and add tun to the list of modules:
sudo gedit /etc/modules

But I still can't connect - it says "error: /usr/sbin/vpnc binding to port 500: permission denied". Off to make my own pleas for help ...

---

### Post by tehownt on 2006-07-26
Use sudo kvpnc when launching it so as to allow you to bind the port 500.

---

