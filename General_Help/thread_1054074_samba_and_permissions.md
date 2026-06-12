---
title: "samba and permissions"
date: 2009-01-29
forum: General Help
---

### Post by dphirschler on 2009-01-29
I have just set up a dedicated file server using Ubuntu 8.10, however, I am having difficulties with permissions.  The computer is set up as follows:

P3 733MHz
10GB hdd (sdb) for the OS
500GB hdd (sda) for storage

The 500GB hdd is mounted in fstab with the following line:

```
/dev/sda1 /media/store ext3 defaults 0 0
```

Here is my smb.conf:

```
[global]
    netbios name = SERVER1
#   server string = %h server (Samba, Ubuntu)
    server string = 
    workgroup = HOME
    announce version = 5.0

    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    guest account = nobody
    null passwords = yes

    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes


# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

#;   interfaces = 127.0.0.0/8 eth0
#    interfaces = lo eth0
#    bind interfaces only = yes

    printing = CUPS
    printcap name = CUPS

    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
    panic action = /usr/share/samba/panic-action %d




#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no
    read only = no
    create mask = 0755
    directory mask = 0755

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[share]
    path = /mnt/store
    comment = File server
    browseable = yes
    writable = yes
    read only = no
    hide dot files = yes
    create mask = 0777
    directory mask = 0777
    veto files = /*.{*}/.*/mail/bin/

    public = yes
    guest ok = yes
#    force user = nobody
#    force group = no group

```

It may not be apparent, but I want this file server to not require a password.  So far I have that working.  The drive shows up in Windows and lets me browse and read the files, but I cannot create a directory.  I am almost certain it has to do with permissions but I just don't know how to fix this.

I will say this much.  When I uncomment the last two lines in smb.conf (force user and force group) I cannot even get into the share from a Windows PC.

Please, give me some direction so I can fix this.  I really want this machine to be a useful file server on my network.


Darryl

---

### Post by dphirschler on 2009-01-30
OK, I've fooled around a little with the smb.conf.  I commented out "wins support = yes" and uncommented "force user = nobody" and "force group = nogroup".  And I've done a little testing with the server and here are the results.  

1) I was able to create directories under the main "\share" directory from a Windows PC.  I thought I was home free at this point.

2) I was able to move files over to the server from another smb share through smbclient.  I do not like smbclient, but it did the trick.

3) I was not able to move files to the server from a Windows PC into any of the directories, only into the main "\share" directory.  A freshly moved file from a Windows PC shows up like so with 'ls -l' "-rwxrw-rw- 1 nobody nogroup ..."; the directory that I am unable to move files into shows up as "drwxr-xr-x  5 nobody nogroup".  A freshly created directory from a Windows PS (right-click, 'new folder') shows up as "drwxrwxrwx  2 nobody nogroup".

4) This is what concerns me most.  I logged into my server and tried to do a 'cat /etc/samba/smb.conf >/mnt/store/smb20090130.conf' and I got "Permission denied".  Then I tried it with 'sudo' and got the same thing.  It wasn't until I did 'sudo su' that I was able to do that command.  why?

So now I have three questions.  Should I change 'create mask' and 'directory mask' to 0777 (or something else)?  What do I need to change in order to be able to write to the directories?  Why do I need to be super user in order to do anything?


Darryl

---

### Post by dreamie on 2009-03-29
Hi!

I have the same problem. I've Samba set up and have no trouble writing to the folders from a Windows machine. 

But from the server itself I can't write to to any of the folders with nogroup:nobody permissions set.

What I want to do is download files from a browser and put them in a samba folder with the nogroup:nobody permissions set, how could this be done?

---

