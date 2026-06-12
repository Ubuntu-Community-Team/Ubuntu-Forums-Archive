---
title: "smbpasswd error"
date: 2005-01-07
forum: Desktop Environments
---

### Post by Dustin Wyatt on 2005-01-07
> 
 $ sudo smbpasswd -a Dustin
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user Dustin. Does this user exist in the UNIX password database ?
Failed to modify password entry for user Dustin

I can't find any guidance on this.  Even google fails to turn up anything helpful.  :(

---

### Post by fng on 2005-01-08
Could you post the output of 'cat /etc/passwd | grep Dustin' ?

---

### Post by Dustin Wyatt on 2005-01-08
[QUOTE=fng]Could you post the output of 'cat /etc/passwd | grep Dustin' ?[/QUOTE]
 I get no output from that.  I tried it both with and without a preceding 'sudo'.  I'm typing the command correctly because when I use "thermo" instead of "Dustin" I get results.  (thermo is the name of my account on the linux box)

Could this be because my username on the linux box is different from the username on the Windows box?  (I'm trying to setup samba to allow access to the linux box from Windows machines.)

---

### Post by Dustin Wyatt on 2005-01-11
[QUOTE=Dustin Wyatt]I get no output from that.  I tried it both with and without a preceding 'sudo'.  I'm typing the command correctly because when I use "thermo" instead of "Dustin" I get results.  (thermo is the name of my account on the linux box)

Could this be because my username on the linux box is different from the username on the Windows box?  (I'm trying to setup samba to allow access to the linux box from Windows machines.)[/QUOTE]
 bumpity, bump, bump?  :p

---

### Post by jiyuu0 on 2005-01-11
[QUOTE=Dustin Wyatt]I get no output from that.  I tried it both with and without a preceding 'sudo'.  I'm typing the command correctly because when I use "thermo" instead of "Dustin" I get results.  (thermo is the name of my account on the linux box)

Could this be because my username on the linux box is different from the username on the Windows box?  (I'm trying to setup samba to allow access to the linux box from Windows machines.)[/QUOTE]

yes... when u smbpasswd -a username... the username must exist on ur linux box

if u need to map thermo with dustin... you can do it with smbusers

there is a howto on this at:
[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)

---

### Post by Dustin Wyatt on 2005-01-11
[QUOTE=jiyuu0]yes... when u smbpasswd -a username... the username must exist on ur linux box

if u need to map thermo with dustin... you can do it with smbusers

there is a howto on this at:
[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)[/QUOTE]
 ahh...Thank you.

---

