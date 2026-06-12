---
title: "How do I mount a Samba share under Xubuntu?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Brian Kendig on 2006-06-08
I'm using Xubuntu 6.06. How do I mount a Samba shared volume across my network?

I've tried going into the File Manager -> Go -> Open Location and typing "//servername/share", but the Open button is greyed out.

---

### Post by karthik085 on 2006-06-08
[QUOTE=Brian Kendig]I'm using Xubuntu 6.06. How do I mount a Samba shared volume across my network?

I've tried going into the File Manager -> Go -> Open Location and typing "//servername/share", but the Open button is greyed out.[/QUOTE]
Use Xfsamba or Xffm(if your Xfce version is above 4.4)

---

### Post by Tamihania on 2006-06-08
[quote=Brian Kendig]I'm using Xubuntu 6.06. How do I mount a Samba shared volume across my network?

I've tried going into the File Manager -> Go -> Open Location and typing "//servername/share", but the Open button is greyed out.[/quote]

...or go to System->Shared folders - you will be promt to install SMB(Windows) or/and NFS(Linux) - after succesful installation you'll be able to set SMB or NFS shares.

Good luck,
tami :)

---

### Post by Brian Kendig on 2006-06-08
karthik085 - What package is xffm in? It doesn't appear to be part of the Xubuntu distribution?

Thank you for the tip, Tamihania - I went ahead and did that, and it installed SMB, but where do I specify the share name and username/password for the network drive I want to mount? It looks like "Shared Folders" is for publishing shares, not mounting them?

---

### Post by Chordonblue on 2006-06-09
I'm having this issue too. It was much easier under Ubuntu. I did install the SMB option under 'Shares', but not sure how to connect to a Windows share at this point. 

I'm in the process of converting 40 machines to Xubuntu (well, I hope to), but this is a showstopper for us at this point. I've managed to get everything else where I want it.  :)

..CrdnBlu

---

### Post by jongkind on 2006-06-09
[QUOTE=Chordonblue]I'm having this issue too. It was much easier under Ubuntu. I did install the SMB option under 'Shares', but not sure how to connect to a Windows share at this point. 

I'm in the process of converting 40 machines to Xubuntu (well, I hope to), but this is a showstopper for us at this point. I've managed to get everything else where I want it.  :)

..CrdnBlu[/QUOTE]

I had the same issue on one of our older machines. After installing the unbuntu-desktop package I was able to use Samba in Xubuntu.

---

### Post by karthik085 on 2006-06-09
[QUOTE=Brian Kendig]karthik085 - What package is xffm in? It doesn't appear to be part of the Xubuntu distribution?

Thank you for the tip, Tamihania - I went ahead and did that, and it installed SMB, but where do I specify the share name and username/password for the network drive I want to mount? It looks like "Shared Folders" is for publishing shares, not mounting them?[/QUOTE]
If your Xfce version is 4.4, which is still in development stages and not available among Ubuntu respositories, you will find xffm with the ability to browse samba networks there. If you have earlier versions, xffm won't be help to you. Just use xfsamba.

---

### Post by Brian Kendig on 2006-06-20
What package is xfsamba in?

---

### Post by karthik085 on 2006-06-20
I think it is included when you install Xubuntu. You should see in the menu, or open a terminal and type xfsamba.

If it is not installed, try apt-cache search xfsamba. It will give you the name(s) of the package related to it. Install the necessary one(s)
apt-get install <package name(s)>

[QUOTE=Brian Kendig]What package is xfsamba in?[/QUOTE]

---

### Post by Brian Kendig on 2006-06-26
It's not part of the Xubuntu 6.06 distribution, and "apt-cache search xfsamba" turns up nothing.

---

### Post by karthik085 on 2006-06-26
apt-cache search xfsamba, gives me:
xffm4 - File manager for the Xfce4 desktop environment

xfsamba is part of xffm4. So, to install:
sudo apt-get install xffm4

You need to add few respositories, to your sources.list. You can manually edit /etc/apt/sources.list. Check my attached sources.list.

You can easily do this with front-end client too. Go to System -> Administration -> Software Properties. Click on Add. Enable the ones you want.



[QUOTE=Brian Kendig]It's not part of the Xubuntu 6.06 distribution, and "apt-cache search xfsamba" turns up nothing.[/QUOTE]

---

### Post by xoros on 2006-06-26
> Substitute the appropriate host name, share and mount point for your systems.
Example: Mount a Windows share on your Linux system. Enter the following command all on one line.

mount -t smbfs -o username=<Windows system user account>,password=<password> //win2k/docs /mnt/docs

he could do something like that too?

---

