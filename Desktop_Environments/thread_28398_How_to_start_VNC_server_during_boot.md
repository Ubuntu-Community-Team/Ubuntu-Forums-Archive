---
title: "How to start VNC server during boot"
date: 2005-04-20
forum: Desktop Environments
---

### Post by dermotti on 2005-04-20
I spent bout 20 mins searching to no avail on this. 

Right now my VNC is working great AFTER i login. Problem is i dont want to leave my computer logged in at home all the time. Is there a way i can enable VNC server during bootup?

---

### Post by syltty on 2005-04-20
Try if this helps ( I have not tested if this works):

$ cd /etc/init.d

$ sudo -s

change the following command with your username and systemname:
echo 'su - username -c "vncserver :1 -name SystemName -depth 16 -geometry' >> vncstart

$ update-rc.d vncstart defaults

$ exit

and reboot.

---

### Post by dermotti on 2005-04-20
Ill give it a try tnite and see how it goes :-)

---

