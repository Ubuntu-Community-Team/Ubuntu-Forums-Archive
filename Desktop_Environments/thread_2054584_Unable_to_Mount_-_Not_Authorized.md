---
title: "Unable to Mount - Not Authorized"
date: 2012-09-07
forum: Desktop Environments
---

### Post by Jesulinux on 2012-09-07
Hi all,

I've just started to test Ubuntu for the firs time, I'm trying to setup Ubuntu 12.04 LTS over VMWare Player 3.1.5, everything is working fine but I was not able to install VMWare tools, I've realized that the installation created a new virtual CD device but, the problem I've found is that I can't mount any device (CDROM, USB, ...) when I try to access a pop up appears saying "UNABLE TO MOUNT Ubuntu 12.04.1 LTS i386

Changed the rights of my user to have full access to devices but the same problem still remains.

I've been searching any solution to the problem over internet and forums but I can't find any solution.

Can you, please, help me?

Cheers,

---

### Post by Bashing-om on 2012-09-07
just a thought: are you not using admistrative authority to mount devices ?
are you making a mount point ?
```

sudo mkdir /mnt/data
sudo mount /dev/sdb1 /mnt/data

```
as one example.

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by youngunix on 2012-09-11
The vmware-tools CD, should be mounted when you chose to install from the drop down menu of the vmware player, so it should show on your desktop(in the Ubuntu).
Here is what I did to install it on mine:
```
sudo -i   #drop in to root enviroment
cd /media/VMware Tools #or whatever the name of it at the time
/media/VMware Tools: tar -xvf VMwareTools-version-.tar.gz /home/user/Downloads  #you can extract it anywhere you want
cd /home/user/Downloads/vmware-tools-distrib   #cd to the folder you extracted
perl vmware-install.pl   #or ./vmware-install.pl, it is a guided installation

```

---

### Post by Jesulinux on 2012-09-14
> **youngunix said:**
> The vmware-tools CD, should be mounted when you chose to install from the drop down menu of the vmware player, so it should show on your desktop(in the Ubuntu).
Here is what I did to install it on mine:
```
sudo -i   #drop in to root enviroment
cd /media/VMware Tools #or whatever the name of it at the time
/media/VMware Tools: tar -xvf VMwareTools-version-.tar.gz /home/user/Downloads  #you can extract it anywhere you want
cd /home/user/Downloads/vmware-tools-distrib   #cd to the folder you extracted
perl vmware-install.pl   #or ./vmware-install.pl, it is a guided installation

```

Hi all,

Here comes the problem, just when I execute Install VMWare tools, a new device called "VMWare Tools" is displayed, when trying to acces to the device a popup appears saying "Unable to mount VMWare Tools Not Authorized", that message is displayed when trying to access to any other device CDROM, USB or others, they are displayed but can't get access.

Cheers,

---

