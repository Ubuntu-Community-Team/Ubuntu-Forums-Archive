---
title: "Sharing samba as guest AND user"
date: 2011-09-30
forum: Desktop Environments
---

### Post by Azyx on 2011-09-30
Hi.
I can share a folder at user AND guest, but when I connect it always be as guest, with no writing permissions. How do I access as user with pemission, when I have checked both:

X Allow others to create and delete files

X Guest access (for people without a user account

For instance in normal use I don't need write access, but when I do I want to log in as user.

/Cheers.

PS. I have 10.04 LTS on the sharing computer.

---

### Post by Morbius1 on 2011-09-30
Please post the output of each of the following commands:
```
net usershare info --long
testparm -s
```

---

### Post by Azyx on 2011-09-30
> **Morbius1 said:**
> Please post the output of each of the following commands:
```
net usershare info --long
testparm -s
```

Here it is: 

```
Azyx@DasDatorn:~$ net usershare info --long
[gis]
path=/home/Azyx/Desktop/Azyx/120GB/GIS
comment=
usershare_acl=Everyone:F,
guest_ok=y

Azyx@DasDatorn:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
Azyx@DasDatorn:~$ 
```

I have mounted the hdd 120GB in a folder in my home-directory, so the disk appeares in both the my  home-folder AND on the desktop.

/Cheers

---

### Post by Morbius1 on 2011-09-30
I don't think you will be able to pull off your specific requirement ( most of the time r/o guest access but r/w when needed for a specific user ) using usershares  ( i.e., via Nautilus ). I propose the following: share it twice using a different share name using a Classic samba share:

[1] Go back into Nautilus and unshare the folder.

[2] Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```[3] Add the following lines to the end of smb.conf:
```
[gis-guest]
path=/home/Azyx/Desktop/Azyx/120GB/GIS
read only = yes
guest ok = yes
[gis]
path=/home/Azyx/Desktop/Azyx/120GB/GIS
read only = no
guest ok = no
valid users = Azyx
```[4] Restart samba:
```
sudo service smbd restart
```Every time you restart samba the network has a fit so give it a few minutes and see if this fulfills your requirement.

---

### Post by Azyx on 2011-09-30
Working great :)
Thanx a lot 

By the way. Do you know how I remove the link made i nautilus under 'Places'

/Cheers

---

### Post by Morbius1 on 2011-09-30
Right click the link and select "remove"

---

### Post by Azyx on 2011-09-30
> **Morbius1 said:**
> Right click the link and select "remove"

No, right-click work as normal-click :(. Ahh. but i work if I activated side-planel and do it there. Thanx again. /cheers

---

