---
title: "Extra Desktop effects not working"
date: 2007-12-14
forum: Desktop Effects &amp; Customization
---

### Post by ShutItDown on 2007-12-14
When i installed 7.1 at my IT class the EXTRA desktop effects will not work. it says something is wrong with my graphics card but its installed and dont know what to do. Any advice? something about the config files or something i heard from anotherstudent in hte P.M. class.

---

### Post by Netrunner on 2007-12-14
check if you have 3d acceleration.
and direct rendering: Yes

---

### Post by ShutItDown on 2007-12-14
how would i go about doing this?

---

### Post by daengbo on 2007-12-14
Go to System -> Preferences -> Hardware information and tell us what the graphics chipset is.

---

### Post by kshane on 2007-12-14
> **ShutItDown said:**
> how would i go about doing this?

In terminal, type: 

```
 glxinfo |grep direct
```

---

### Post by ShutItDown on 2008-01-07
sorry i just got back in her from break.

 i have a Geforce 8400 GS

glxinfo |grep direct      came up with this 

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
ian@Linux5:~$ 


now what?

---

### Post by kshane on 2008-01-07
> **ShutItDown said:**
> sorry i just got back in her from break.

 i have a Geforce 8400 GS

glxinfo |grep direct      came up with this 

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
ian@Linux5:~$ 


now what?

You need to install/reinstall your Nvidia drivers...  You're not using them...

Kevin

---

### Post by ShutItDown on 2008-01-08
it says it is not supported. is there an update or something? i tried using envy but when i double clicked it unpack it said it wont support it. any code for that? i know someone haas got it to work out there..

---

