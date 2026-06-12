---
title: "Specify directory on network hard drive for amaroK"
date: 2006-08-02
forum: Desktop Environments
---

### Post by srunni on 2006-08-02
Is there any way for me to specify a directory on another computer in my LAN as the default directory for amaroK? If so, can this be done through the "First-Run Wizard"?

---

### Post by orb9220 on 2006-08-02
goto your config amorak settings collections. All the drives should be listed
just drill down till you find the drive and folder you want and put a checkmark for it.

Amorak then should start scanning and add them to the library.

---

### Post by Ares Drake on 2006-08-02
I don't know if it is easily possible, however you can get arround your problem by mounting your network share as a local folder. For details, see here: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

Good luck!

---

### Post by srunni on 2006-08-02
Well, I'm pretty sure that I've already mounted the hard drive I want to access. There's an icon on my desktop for the shares on the other computer (it's a Windoze). To get rid of the icon, I have to right click and choose "unmount". Maybe this means that I've already mounted it? If so, where on the local hard drive is this mount located?

EDIT: there are no directories or files under "/mnt"

---

### Post by srunni on 2006-08-02
Any ideas?

---

### Post by srunni on 2006-08-02
Still haven't found a solution. Does anyone know where a mounted share is under the filesystem?

---

### Post by srunni on 2006-08-02
I get the following error when using the method provided at the link that Ares Drake posted:

mount: wrong fs type, bad option, bad superblock on //192.168.1.100/Tunez,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I get it when fstab is remounted.

---

### Post by Wormsie on 2006-08-18
Possibly /media

---

### Post by srunni on 2006-08-19
> **Wormsie said:**
> Possibly /media

For what?

---

### Post by edo152 on 2006-09-06
> **srunni said:**
> Well, I'm pretty sure that I've already mounted the hard drive I want to access. There's an icon on my desktop for the shares on the other computer (it's a Windoze). To get rid of the icon, I have to right click and choose "unmount". Maybe this means that I've already mounted it? If so, where on the local hard drive is this mount located?

EDIT: there are no directories or files under "/mnt"

The problem here is that when you do thisnone of the network drives are listed.  Is there a command to add so that Amorak can see the network drives?

---

### Post by edo152 on 2006-09-06
> **srunni said:**
> Well, I'm pretty sure that I've already mounted the hard drive I want to access. There's an icon on my desktop for the shares on the other computer (it's a Windoze). To get rid of the icon, I have to right click and choose "unmount". Maybe this means that I've already mounted it? If so, where on the local hard drive is this mount located?

EDIT: there are no directories or files under "/mnt"

The problem here is that when you do thisnone of the network drives are listed.  Is there a command to add so that Amorak can see the network drives?

---

### Post by srunni on 2006-09-06
I don't think there is a command for that. But I may be wrong, as I tried to do this on Amarok 1.3.9, and the repos have finally updated, so it's now 1.4.2. Also, maybe a request to the devs might work?

---

