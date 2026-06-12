---
title: "Ununtu 10.04 on VirtualBox screen resolution problems"
date: 2010-05-19
forum: Desktop Environments
---

### Post by neo_in_matrix on 2010-05-19
I have a fresh new installation of 10.04 inside VirtualBox. The problems are:

1. I have System->Preferences->Monitors, but not Display menu. I'm not sure if it's 10.04 new thing.
2. Monitor Preferences only have 800x600 and 640x480.

But apparently the virtual driver supports 1024x768 at least. How can I change that? It's way too small to use 800x600.

---

### Post by durzagott on 2010-05-19
> **neo_in_matrix said:**
> How can I change that? It's way too small to use 800x600.

Have you installed the VirtualboxAdditions?

---

### Post by neo_in_matrix on 2010-05-20
I tried to install the Additions. After mounting the ISO, I tried to run the command and got:
bash: ./VBoxLinuxAdditions-x86.run: Permission denied

---

### Post by beavis5551 on 2010-05-20
did you try it with 'sudo'?
 
AFAIK you need to be root.

---

### Post by neo_in_matrix on 2010-05-20
:confused: Yeah. I'm a Windows user for more than 10 years and have get addicted to it. I'm not comfortable with all those manual configuration in Linux. I have to do it again, again and again.

Anyway, I found out that I did not add exec option to fstab, the result is:

/dev/cdrom  /media/cdrom  iso9660  ro,user,noauto,exec,unhide

I'm installing the Additions. I'll see if the resolution list will differ than before.

Yeah... I get 1024x768 affer rebooting.

---

