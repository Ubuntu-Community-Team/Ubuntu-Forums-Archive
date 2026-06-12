---
title: "Remote Desktop"
date: 2009-06-17
forum: General Help
---

### Post by gogreenpower on 2009-06-17
im trying to connect via ubuntu 9.04 built in remote desktop apps to another ubuntu 9.04 machine on my home network. i can connect to it and see it, my problem is all my commands are working on the remotely connected computer but i get no visual feed back on the computer i use to connect. im sitting right next it and can see the mouse move and me open up windows etc. but on the machine im using to connect it shows nothing. i've tried vnc as well with the same result. and i have desktop effects set to none.

Any suggestions?

---

### Post by ptn107 on 2009-06-17
On the machine you wish to connect to (the remote machine) set up System -> Preferences -> Remote Desktop as you wish.  On the machine you want to access from open Applications -> Internet -> Remote Desktop Viewer.  The remote desktop you set up first will appear on the left under bookmarks automatically.  Just make sure you have no [local] firewall enabled on either machine.

---

### Post by gogreenpower on 2009-06-17
> **ptn107 said:**
> On the machine you wish to connect to (the remote machine) set up System -> Preferences -> Remote Desktop as you wish

done, allow others to view and control, no password.


On the machine you want to access from open Applications -> Internet -> Remote Desktop Viewer.  The remote desktop you set up first will appear on the left under bookmarks automatically.  

bookmark is there.


Just make sure you have no [local] firewall enabled on either machine. 

i dont think so, but how could i check? i have never installed any firewalls

---

### Post by redilyn on 2009-06-18
It most likely is not a firewall issue since your commands are being sent to the remote system.

Regardless, you can check to see if ufw is enabled by doing the following:

Open a terminal and type
```

sudo ufw status

```

---

### Post by gogreenpower on 2009-06-18
both machines are "inactive"

---

### Post by redilyn on 2009-06-18
Have you tried to remote desktop from the remote computer to your local computer to see if it works correctly.

I know it won't solve your problem but it might help narrow it down.

---

### Post by gogreenpower on 2009-06-18
ok it does works back the other way, strange? the box im trying to connect to is x64 from a x32 machine. would that do anything? and the x64 machine is a fresh install

---

### Post by ptn107 on 2009-06-18
CPU architecture shouldn't matter.

---

