---
title: "Block Control Problems"
date: 2009-06-06
forum: General Help
---

### Post by Raymen864 on 2009-06-06
Hey Ubuntu Users

I'm configuring block control on my Linux, yet there sees to be a "Permission denied" Problem. 

n****@N****-PC:~$ sudo blockcontrol start
 * Starting IP block daemon moblock                                             
/usr/bin/blockcontrol: 190: cannot create /var/log/blockcontrol.log: Permission denied

I searched the forum for a problem like this
I don't think that it is a blockcontrol problem, but more of a linux problem

I am running Ubuntu 9.04 Jaunty

any sugestions?

---

### Post by Legace on 2009-06-06
Try:
```
sudo -i
```

Then:
```
blockcontrol start
```

---

### Post by jre on 2009-06-06
further you may check the permissions of /var/log:
```
ls -al /var/
```
should show for the "log" directory
```
d**rwx**r-xr-x 15 **root** root  12288 2009-06-06 12:41 log
```

Check the fat marked stuff.

---

