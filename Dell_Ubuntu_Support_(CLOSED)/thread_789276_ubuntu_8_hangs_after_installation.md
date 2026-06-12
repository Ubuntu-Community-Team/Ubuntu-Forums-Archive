---
title: "ubuntu 8 hangs after installation"
date: 2008-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ajosep01 on 2008-05-10
I just upgrade my dell Inspiron600m to ubuntu 8.The install went flawless. However, after i enter the user and password i get an orange screen and the system just hangs and  gets no where. I the nfix nothing is working. Any idea? Have anyone run into this.

---

### Post by mybeat on 2008-05-13
I have the same problem with ubuntu 8.04 on Dell latitude d630.
I think it somehow related to xorg packages, i've also had the same problem on debian unstable 2 week's ago, but now after apt get update & upgrade everything is working fine.

---

### Post by njparton on 2008-05-13
ajosep01, hit CTRL-ALT-backspace together and this should get you to a shell prompt.
 
Then try the following:
 
```
 
sudo /etc/init.d/gdm stop
sudo apt-get update
sudo apt-get upgrade
sudo reboot

```

---

