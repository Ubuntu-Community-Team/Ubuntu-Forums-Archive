---
title: "Samba"
date: 2005-11-27
forum: Desktop Environments
---

### Post by CharlieC on 2005-11-27
I managed to correctly install samba and my Ubuntu box sees it. My XP box on the same network does not. 
I know that I have to add a user in order for that to work but I am not sure of how to do this. I found this in the documentation, is this correct or is there some other way I need to be doing this:

Q: How to mount network folders on boot-up, and allow all users to read/write?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3.

e.g. Assumed that network connections have been configured properly
     Network computer's IP: 192.168.0.1
     Network computer's Username: myusername
     Network computer's Password: mypassword
     Shared folder's name: linux
     Local mount folder: /media/sharename

   4.

sudo mkdir /media/sharename
sudo gedit /root/.smbcredentials

   5. Insert the following lines into the new file

username=myusername
password=mypassword

   6. Save the edited file (sample)
   7.

sudo chmod 700 /root/.smbcredentials
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   8. Append the following line at the end of file

//192.168.0.1/linux        /media/sharename  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0

TIA
Charlie

---

### Post by jeffjanzen on 2005-12-03
i followed these instructions, but it doesn't work for me.  i get this message when i boot up:
```
Usage: mount.smbfs service mountpoint [-n] [-o options,...]
Version 3.0.14a-Ubuntu

Options:
      username=<arg>                  SMB username
      password=<arg>                  SMB password
      credentials=<filename>          file with username/password
      krb                             use kerberos (active directory)
      netbiosname=<arg>               source NetBIOS name
      uid=<arg>                       mount uid or username
      gid=<arg>                       mount gid or groupname
      port=<arg>                      remote SMB port number
      fmask=<arg>                     file umask
      dmask=<arg>                     directory umask
      debug=<arg>                     debug level
      ip=<arg>                        destination host or IP address
      workgroup=<arg>                 workgroup on destination
      sockopt=<arg>                   TCP socket options
      scope=<arg>                     NetBIOS scope
      iocharset=<arg>                 Linux charset (iso8859-1, utf8)
      codepage=<arg>                  server codepage (cp850)
      unicode                         use unicode when communicating with server      lfs                             large file system support
      ttl=<arg>                       dircache time to live
      guest                           don't prompt for a password
      ro                              mount read-only
      rw                              mount read-write

This command is designed to be run from within /bin/mount by giving
the option '-t smbfs'. For example:
  mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test
```
PLEASE HELP!

---

