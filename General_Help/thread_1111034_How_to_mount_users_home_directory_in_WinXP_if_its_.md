---
title: "How to mount users home directory in WinXP if its not in /home in samba"
date: 2009-03-30
forum: General Help
---

### Post by Avinash.Rao on 2009-03-30
Dear all,

I am using Samba as PDC on Ubuntu 8.04 with WinXP clients. All the users home directory is under /home and when the users log in to the domain, their respective home directories are mapped as a network drive as specified in smb.conf file.

I would like to categorize the users home directories under /home for ease of data backup. For example, instead of having all the users under /home, i would like to create new users in /home/accounts/user1. If i do this, the home directories dnt get mapped.

Is there anyway, i can get these home directories mapped as a network drive when they login, if their Home directories is not in /home?? The other option is to use netlogon scripts, but can i do this without executing any scripts?

Thanks
Avinash

---

### Post by Avinash.Rao on 2009-07-02
smb.conf

[global]
    workgroup = SANDBOX
    server string = Samba on SUN
    max log size = 500
    log level = 1

    domain logons = yes
    os level = 65
    prefered master = yes
    domain master = yes
    local master = yes
   
    add machine script = /usr/sbin/useradd -s /bin/false -d /home/nobody %u
    dns proxy =No
    hosts allow = 127. 10.10.10.
    wins support = Yes
    passdb backend = smbpasswd
        security = user
        netbios name = samba
    username map = /etc/sfw/smbusers   

[B][homes]
    comment = Home Dir
    read only = NO
    browseable = NO[/B]

[share]
    comment = test share
    path = /sambashare
    valid users = padma
    create mask = 0765

I have only winXP clients and my ubuntu server is configured to function as PDC.  The users are able to login to the domain and when they login, their home directories are mapped as a network drive without any problem. The **homes** share in the file will map the users directory when users login to the domain and works well. 

I have many user accounts and their home directory is under /home/usernames. I am in need of arranging the users home directory so that i can take proper backup easily. For instance, i want to place 20users home directory belonging to the Accounts department in /home/accounts/username path. I know i can do this in ubuntu, but the main requirement is Mapping these home directories when  users login from WinXP. What will be the entry in the smb.conf file if I change the home directory path to say for example /home/accounts/username. 

I have tried changing the "login path" entry under [homes] section but they network drive doesn't come up.

I hope you are able to understand the question and if i am able to do this, it will be of great help which will ease my backup and other administrative tasks.

Can anybody help me? 
Avinash

---

### Post by Avinash.Rao on 2009-07-03
Has anybody worked with so many users with samba before?

---

