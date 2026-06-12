---
title: "version number"
date: 2005-11-30
forum: Desktop Environments
---

### Post by elwingert on 2005-11-30
Without using Synaptic, how is it possible to check the version number of an installed application from the Terminal.  Can you do it with apt, dpkg, etc...  With redhat I can always run rpm -q <pagename>.  Thanks

---

### Post by frodon on 2005-11-30
Generally all the softwares have a -v option which show the version in use. For exemple this command will return the version of xine : ```
xine -v
```

---

### Post by elwingert on 2005-11-30
Thanks for the response, that way does work, however i was looking for a quicker way then finding the executable then it's version switch.  I was hoping for a simple dkpg -v xine to tell me all of the installed version of xine

[QUOTE=frodon]Generally all the softwares have a -v option which show the version in use. For exemple this command will return the version of xine : ```
xine -v
```[/QUOTE]

---

### Post by oskude on 2005-11-30
apt-cache show <package> | grep "Version"

---

### Post by frodon on 2005-11-30
"dpkg --version" works too if it's what you're looking for.

Here are the details of the dpkg options (you can get it in terminal with the "man dpkg" command) : [http://www.abc.se/home/m10828/webgine1320e_linux/man__H_dpkg.html](http://www.abc.se/home/m10828/webgine1320e_linux/man__H_dpkg.html)

---

### Post by elwingert on 2005-11-30
Is it also possible to show if that particular version is installed?  That appears to show me all the versions no matter if they are installed or not.

---

### Post by oskude on 2005-11-30
dpkg -s <package>

---

### Post by elwingert on 2005-11-30
Perfect, thanks!  sorry i missed that one

---

### Post by oskude on 2005-11-30
was new to me too, i just looked the man pages ;)

---

