---
title: "Help with Samba Configuration"
date: 2009-01-08
forum: General Help
---

### Post by falconed7 on 2009-01-08
Hey everyone!

I have only been using ubuntu (8.04.1) for 1/2 months and have my server up for a while and I followed these guides:
[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

It does the job although it has a very basic explanation of Samba and file permissions.

Basically I am looking at making my smb.conf more 'efficient' by getting rid of the things I don't need. I am also looking to add a guest account with a password with read only access to the 'videos' and 'music' folders.

My current share is in /media/store and I have the following folders that are located in /media/store:
1. documents
2. music
3. other
4. pictures
5. videos

I have 2 users: 'falconed' (me) and 'family' both with read/write access to all folders.

Here is my current smb.conf:

```
[global]
    ; General server settings
    netbios name = wrongserver
    server string =
    workgroup = WRONGGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[share]
    comment = Private Folder
    path = /media/store/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = falconed
    force group = falconed
```

My Questions:
1. I don't have a print server running and assume I can get rid of the CUPS section in the conf?
2. Can someone please explain the different mask numbers as I haven't seen a list/guide on what each number does.
3. How would I create and grant a guest account read-only access to the 'music' and 'video' directories. Would I need to create a whole new share?

Any help will be much appreciated!
Cheers.

---

### Post by jgoguen on 2009-01-08
1. Yes, if you're not sharing printers you can get rid of **printing = cups** and **printcap name = cups**.  You could also add **load printers = no** to explicitly tell Samba to not load your printers.

2. The mask numbers should be taken as four separate numbers put together.  The first one is the setuid/setgid/sticky bit.  Generally, this should be 0 unless you've got a good reason to change it.  The second, third, and fourth numbers are read/write/execute for user, group, and other, respectively.  Read is 4, write is 2, and execute is 1. To combine permissions, add numbers together.  For example, read and write permissions would be 6, or read and execute (but not write) permissions would be 5.  A mask of "0754" would mean:

[LIST]
[*]The sticky bit isn't set, and not setuid or setgid
[*]The owner can read the file, write to the file, and execute the file (4 + 2 + 1 = 7)
[*]Users in the file's assigned group can read and execute the file, but can't write to it (4 + 1 = 5)
[*]Other users can only read the file (4)
[/LIST]


3. I believe your share definition (and also likely the permissions and ownerships of the directory and everything under it) would need some changes.  Here's the minimal smb.conf I would use to achieve this:
```

[global]
    workgroup = WORKGROUP
    server string = %h
    security = user
    map to guest = bad user

[share]
    comment = Shared directory
    path = /media/store/
    browsable = yes
    read only = yes
    guest ok = no
    create mask = 0664
    directory mask = 0775
    write list = falconed, family

```Then, set up a group for Samba users who should be allowed to write to this folder:
```
sudo groupadd sambausers
```Add both yourself (not strictly necessary) and 'family' to this group:
```
sudo usermod -a -G sambausers falconed
sudo usermod -a -G sambausers family
```Set permissions on the shared folder:
```
sudo chown -R falconed:sambausers /media/share/
chmod -R ug=rwX /media/share/
chmod -R o=rX /media/share/
```That makes the directory writable by you and anyone in the 'sambausers' group but no one else.  Now, create your guest user:
```
sudo useradd -c "SAMBA Guest User" -U guest
```That creates a new user named 'guest'.  Now add this user to the SAMBA password file:
```
sudo smbpasswd -a guest
```Enter a password for 'guest' when prompted.  Restart SAMBA and both you and 'family' should be able to log in and write to the SAMBA share, and 'guest' should be able to log in but not write to the share.

---

