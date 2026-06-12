---
title: "How do I uninstall a program?"
date: 2005-03-02
forum: Desktop Environments
---

### Post by cajunaggie on 2005-03-02
There are some programs I've installed that I no longer use. How do I go about getting rid of them?

---

### Post by bored2k on 2005-03-02
[QUOTE=cajunaggie]There are some programs I've installed that I no longer use. How do I go about getting rid of them?[/QUOTE]

Open synaptic [alt+f2 synaptic] in status select installed right clic on ur desired to be gone app and a red X should appear aiming 2 remove .


or from terminal
apt-get remove application.name

or open up aptitude and follow the "semi" gui

---

### Post by spartas on 2005-03-02
Uninstalling depends on if you apt-getted them or compiled them.  If you used apt-get [program], all you need to do it use the following command (as a superuser, of course)

```

apt-get remove {program}

```

If you compiled it, then it's a little trickier.  Most programs come with an uninstall script that you can run in the shell (usually in /opt or wherever you installed it).  

If you downloaded the program and did not have to compile it (e.g. eclipse), you can just remove the directory and any symlinks or launchers that point to the executable.

---

### Post by cajunaggie on 2005-03-03
Thank y'all much.

---

### Post by Mikko Rautiainen on 2006-04-21
How do I uninstall Eclipse? I installed it using apt-get and it is unusably slow. Maybe I'll see to it later if it can be speeded up, but now I'm getting rid of it.

```
sudo apt-get remove eclipse
```
doesn't work, it says the package eclipse could not be found.

---

### Post by Nordoelum on 2006-04-22
[QUOTE=Mikko Rautiainen]How do I uninstall Eclipse? I installed it using apt-get and it is unusably slow. Maybe I'll see to it later if it can be speeded up, but now I'm getting rid of it.

```
sudo apt-get remove eclipse
```
doesn't work, it says the package eclipse could not be found.[/QUOTE]
Searched for eclipse in Synaptic?

---

