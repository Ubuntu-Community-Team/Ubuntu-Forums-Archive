---
title: "Ubuntu, the AD and home drives"
date: 2010-10-05
forum: Desktop Environments
---

### Post by DecemberWolf on 2010-10-05
Hello everyone

we are looking at deploying Ubuntu desktop and laptop machines within a currently Windows based network. As we have everything running on the Active Directory, we are not able to fully migrate just yet. So far we have used likewise-open to authenticate against the AD which works beautifully and we have been able to get VPN working.

we are however stumped at the following issues, and would be very grateful for some advice on what do do!

AD home drives. we need these to map dynamically on log-in and they are not in any way standardised (i.e. being 'clever' doesn't work, we need a proper method of asking the AD what the user's home drive is. in Windows it would be "net use /home" and it maps it all!

Updates through the corporate firewall: everything I have seen would require a username and password to be left somewhere in plaintext, which we cannot allow. is there anything firewall-side we could configure to allow apt-get to do its thing, or to allow sudo credentials to be passed to the firewall when apt-get update-ing from the terminal? we have already set our domain admin group up on sudoers so the credentials would be valid.

many thanks in advance for any and all advice on this!

---

### Post by DecemberWolf on 2010-10-12
bump?

---

### Post by atworkwithjf on 2010-10-12
DecemberWolf,

Great to hear that Likewise-Open is working well for you.

Which version of Windows Server are you running on your DC?  If it is 2008 you have a couple of very nice options here using NFS.

I would also be curious if you really need the users directories to be mounted on demand or if system level mounts would work (i.e mounting via fstab).

atworkwithjf

---

### Post by DecemberWolf on 2010-10-13
Hello, thanks for the reply!

The AD runs on windows server 2003, but I would be interested to hear about the NFS options too as we are considering an upgrade sometime next year to 2008 edition

as for fstab, this doesn't work as different user credentials are needed to access different shares, i.e. each user's personal network drive requires their own username/password to mount it. The main issue is in detecting what a user's home drive is according to the AD, as I can script the rest to get it mounted. Any ideas on polling the AD for the /home drive?

thanks

---

### Post by atworkwithjf on 2010-10-13
2003 or 2003r2?

---

