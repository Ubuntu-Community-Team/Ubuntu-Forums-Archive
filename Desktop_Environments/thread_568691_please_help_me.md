---
title: "please help me"
date: 2007-10-06
forum: Desktop Environments
---

### Post by inumair on 2007-10-06
i am using edubuntu
in the services utility i accidently unchecked the GDM option
and now the comp takes ke to the dos type section(non-graphical) of edubuntu
where i can enter my username and password
can some one tell me how to get back the Graphical Display Manager(GDM)
please

---

### Post by Lord Illidan on 2007-10-06
Try entering this in the terminal :

```
sudo /etc/init.d/gdm restart
```

and you should be able to get in the GUI

---

### Post by Amazona aestiva on 2007-10-06
This helps me:
First configure your Xserver:
```
sudo dpkg-reconfigure xserver-xorg
```
Then restart GDM:
```
sudo dpkg-reconfigure gdm
```

**[COLOR="Red"]First try the second, if it doesn't work do both.[/COLOR]**

---

### Post by inumair on 2007-10-06
the 1st solution worked
u rock lord
thanx

---

