---
title: "VNC and Feisty"
date: 2007-05-14
forum: Desktop Environments
---

### Post by PartisanEntity on 2007-05-14
Anyone know if [these]("https://help.ubuntu.com/community/VNC") instructions are still relevant to Feisty?

For example under the section: **Enabling other computers to Connect to XDM/GDM and start sessions.**

In **Step 2 **it says:
> Create the following file /etc/xinetd.d/vnc

However I checked my **/etc** folder and I do not have a **/xinetd.d** directory to begin with.

Do I just create it or is this HowTo assuming something in advance?

---

### Post by dlehman on 2007-05-14
Well I don't recall doing anything special when I set up vnc, it was back in dapper or edgy when I did it and the same options appear to be in feisty. and I know my vnc setup still works so.....
```

System>Preferences>Remote Desktop 
```


should get the job done

---

### Post by PartisanEntity on 2007-05-14
> **dlehman said:**
> Well I don't recall doing anything special when I set up vnc, it was back in dapper or edgy when I did it and the same options appear to be in feisty. and I know my vnc setup still works so.....
```

System>Preferences>Remote Desktop 
```


should get the job done

Oh I see, so System>Preferences>Remote Desktop is actually VNC ?

---

### Post by dlehman on 2007-05-14
yes but did you want vnc or  did you want XDM/GDM connection never tried that through vnc I just use 
```

System>Administration>Login Window
``` then goto the remote tab  

and then from gdm on a remote machine choose options  and remote login via  xdmcp 

I will have to look into starting a new session like that with vnc that is interesting 
and I don't have the 
```
/etc/xinetd.d/vnc
``` file and plain vnc works fine

hope thats what your looking for

---

### Post by PartisanEntity on 2007-05-14
Sorry I don't know much about this, but I would like to log into my Ubuntu desktop from my Windows office computer.

What's the best way to do that?

---

### Post by PartisanEntity on 2007-05-17
Follow up:

```
System>Preferences>Remote Desktop
```

...was actually what I was looking for. It worked from another Ubuntu machine, so far I have not tried it through a Windows machine.

Note: There is however a bug, when you restart, the remote-desktop password will not work and you have to manually enter it again in order to be able to use this password from a remote machine.

Otherwise it worked very nicely.

---

### Post by andytx on 2007-05-17
I have questions,
why VNCserver for windows default port is 5900; For linux is 5500.
I have a  reverse connect that I was made deault port is  5900 for windows.But I when I run Vncviewer listen on ubuntu, the port is 5500. How can I set the Vncviewier listen  port to 5900

Thanks

---

