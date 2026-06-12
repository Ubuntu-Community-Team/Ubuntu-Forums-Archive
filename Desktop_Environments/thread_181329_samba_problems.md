---
title: "samba problems"
date: 2006-05-24
forum: Desktop Environments
---

### Post by raovq on 2006-05-24
i am trying to share folders between two ubuntu computers, with windows xp being supported.

first, ill show you my smb.conf file-

```

[global]
workgroup = workgroup
netbios name = guy
encrypt passwords = yes
security = share
wins support = yes
server string = guy

[homes]
read only = no
browseable = no

[downloads]
path = /home/guy/Downloads
browseable = yes
write list = guy
available = yes
public = yes
writable = no

```
and the other computer

```

[global]
workgroup = workgroup
netbios name = mum
wins support = yes
encrypt passwords = yes
security = share
server string = mum


[homes]
read only = no
browseable = no

[downloads]
path = /home/guy/Downloads
browseable = yes
available = yes
writelist = yes
public = yes
writable = no

```

before anyone asks, yes, there are folders named the same thing.

testparm has no issues with either.

```

ubuntu:~/Downloads> smbtree
Password:
WORKGROUP
        \\MUM                           mum
                \\MUM\ADMIN$            IPC Service (mum)
                \\MUM\IPC$              IPC Service (mum)
                \\MUM\downloads
        \\GUY                           guy
                \\GUY\ADMIN$            IPC Service (guy)
                \\GUY\IPC$              IPC Service (guy)
                \\GUY\downloads

```

it is the same on both.

now, here is the problem. the downloads folder on the 'mum' cannot be accessed. from the first computer or itself. both download folders have 755 permissions and the correct path.

the computer 'guy' cannot access the network, even though smbtree shows it. when  i go to network places, workgroup does not show up.

that is about all the information i can think of, feel free to ask any questions.

thanks in advance for any suggestions.

---

### Post by dmizer on 2006-05-24
smbconf looks good.  that's most of the battle.  you'll just need to create a space for your mounts in fstab, and mount via command line with smbmount.

create a folder in /media named whatever you want your share to be named (ex. mine is sentra, you might like guy or mum accordingly)
then change the permissions of /media/whateveryoucalledit so that your user has permissions.

then mount it from the cli.  mine works like so:
```
smbmount //192.168.0.250/shared /media/sentra -o username=****,password=****
```
then you will get an icon on your desktop showing your shared folder.

---

### Post by raovq on 2006-05-24
im getting a "The folder contents could not be displayed." error when i browse to the downloads directory on "mum" through the places menu. ive checked the directory is there, and the permissions are 755, and its not empty. all the directories on 'guy' work perfectly. im a tad confused.

---

### Post by dmizer on 2006-05-24
yeah ... i am actually still having various problems with samba.  it needs a good gui configuration, because it's something of an enigma.

the help in the following thread is what finally got me able to at least view the files though: [http://ubuntuforums.org/showthread.php?t=169660](http://ubuntuforums.org/showthread.php?t=169660) ... maybe you'll find something in there of use to you.

---

### Post by raovq on 2006-05-24
im guessing there is more that needs to be configured, some random missing file, because i would have assumed that these two exact same installations of samba with the exact same configurations would... behave the same.

---

