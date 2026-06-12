---
title: "Two Topics in One (Backup and Startup)"
date: 2005-08-08
forum: Desktop Environments
---

### Post by theQmaster on 2005-08-08
Hi,

I do have two questions one about backup and one about creating a default startup with selective daemons.


Backup
---------
1. What's the software needed to do backups.
2. What are the supported options tape, cd ? Currenly I have a CD Burner HP 9350i. How do I test if it can burn ? 

I will be great if I'd be able to have a backup process that runs incremently every other day or week that will back up my data. What's my best choice for doing that


Startup
---------
How do I change the default startup so it will include only the selected services ?
I need besides the networking only tomcat, apache and postgresql services to be active, no other daemons. In same time i would be nice to have a different startup that would allow me to boot with X Windows started. Is all this possible ?


Thanks,
Q

---

### Post by amohanty on 2005-08-08
> How do I change the default startup so it will include only the selected services ? 

Look for BootupManager aka BUM

> In same time i would be nice to have a different startup that would allow me to boot with X Windows started 

Do you have a server install? If so you would need to install xorg and gnome or alternatively ubuntu-desktop which is an all in one. If you already have it then just add startx to your .bashrc,

AM

---

### Post by theQmaster on 2005-08-09
Currenly I have Kubuntu with KDE and GNome running. I installed them to easy manage system and files.

The machine is meant to be a server though - so, once I finish instalation and configuration I'd like to have several boot options.

E.g.
default boot entry - the bare minimum services - server mode
xwindows - all needed services to boot up in graphics mode.


Hope this clarifies this.

I will look into BUM to see if it can help me.


What about backup options ?

---

