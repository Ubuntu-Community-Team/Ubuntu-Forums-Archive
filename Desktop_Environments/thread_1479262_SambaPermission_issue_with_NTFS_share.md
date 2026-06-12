---
title: "Samba/Permission issue with NTFS share"
date: 2010-05-10
forum: Desktop Environments
---

### Post by Sjorris on 2010-05-10
Hi all,

I've been trying for several days to get my samba shares (which worked under 9.10 in the exact same setup), and I keep getting the same error.

I'm running 10.04 x86 Desktop, and I'm running the newest samba. I have three drives (aside from the partitions ubuntu is running on), all formatted in NTFS format (the latest ntfs-3g packet is present).

```
[global]
workgroup = workgroup
server string = %h server (Samba %v)
dns proxy = no

log file = /dev/null
log level = 0
syslog = 0
panic action = /usr/share/samba/panic-action %d

security = user
encrypt passwords = true
passdb backend = tdbsam
unix password sync = yes
obey pam restrictions = yes
invalid users = root
map to guest = Bad User

passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

os level = 22
```and several shares as following ```
[Name]
comment = generic comment
path = /media/HD/SharedFolder
browsable = yes
guest ok = yes
read only = yes
admin users = joris
```These shares are all on NTFS drives. 

Now, I get the following error reported in my log.user files for all users (log.smb is without any errors, the folder in this error may vary):
```
[2010/05/10 13:55:09,  0] smbd/service.c:988(make_connection_snum)
  canonicalize_connect_path failed for service Muziek, path /media/Data_HD1/Muziek
```Since I had a hunch it had to do with NTFS permissions, I tried an ext4 share (with the same options). If trying to login to this share, it asks me to authenticate (which is odd, since the username and password for the (Windows) machine trying to authenticate is an admin user on the Ubuntu machine, and unix password sync = yes). Also, smbpasswd returns ```
cli_pipe_validate_current_pdu: RPC fault code DCERPC_FAULT_OP_RNG_ERROR received from host 127.0.0.1!
machine 127.0.0.1 rejected the password change: Error was : NT code 0x1c010002.
``` which, as far as I know, is a 'wrong password' error, while I'm 100% sure the password is correct.

I've tried a lot of different options, and I'm all out of luck. I hope somebody can help me!

---

### Post by robsablah on 2010-09-19
bump - same issue

has something changed since jaunty.... my config file was working fine .... same external HDDs

---

### Post by luvshines on 2010-09-19
Have you checked the permissions of all the directory upto / in your shared path ?

You may have a look at:
[http://ubuntuforums.org/showthread.php?t=1439582](http://ubuntuforums.org/showthread.php?t=1439582)

---

### Post by robsablah on 2010-09-20
hey,

thanks for getting back to me

ran a 
chmod -R 0755 /media/drive/

and i restart samba after every change
'still nutin' - as the young kids say :P
any ideas

---

### Post by luvshines on 2010-09-20
When you said

```

cli_pipe_validate_current_pdu: RPC fault code DCERPC_FAULT_OP_RNG_ERROR received from host 127.0.0.1!
machine 127.0.0.1 rejected the password change: Error was : NT code 0x1c010002.

```

Did you try smbpasswd command as the user itself or smbpasswd -a <user> as the root ?

---

