---
title: "Mounting a network folder"
date: 2006-07-11
forum: Desktop Environments
---

### Post by Dearhell on 2006-07-11
I have a laptop with Ubuntu and there I have a shared folder configured with samba.

It works fine from windows, I type the laptop ip in the Internet Explorer like this:

> \\192.168.1.6

And it appears the Laptop's shared folder and there I can move the files that I want without any problem. 

Now, the problem comes when I want to mount that shared folder from my computer (that also has ubuntu).

I have tried this:

> mount //192.168.1.6/public laptop/ -t ext3


But it says:

> mount: the special dispositive //192.168.1.6/public doesnt exist

Also I have tried to access that folder through the firefox typing this:

> smb://192.168.1.6/public

It works fine, but in this way you only can download files from the shared folder, and not to move files to that folder, that it's exactly what I want

---

### Post by Thund3rstruck on 2006-07-11
you have to mount it as a smb filesystem, not ext3

```

$sudo mount -t smbfs -o username=Username,password=Password //192.168.1.6/public /mnt/laptop

```

---

### Post by Dearhell on 2006-07-11
It displays:

> mount: file system type wrong, option wrong, superblock wrong in //192.168.1.6/public, code page it's missing or any other error

In some cases you can find information in syslog, try dmesg | tail

dmesg | tail displays this:

> [17219928.312000] smb_fill_super: missing data argument
[17219932.068000] smb_fill_super: missing data argument
[17219966.936000] smb_fill_super: missing data argument
[17219978.308000] smb_fill_super: missing data argument
[17219980.772000] smb_fill_super: missing data argument
[17219982.104000] smb_fill_super: missing data argument
[17219997.292000] smb_fill_super: missing data argument
[17220011.944000] smb_fill_super: missing data argument
[17220018.804000] smb_fill_super: missing data argument
[17220059.016000] smb_fill_super: missing data argument


I have typed this:

> mount -t smbfs //192.168.1.6/public laptop/


I didn't specify the username and password option, because I have the samba security in share mode, and not in user mode (it doesn't need any passwords), but anyway the warning display wasn't about that

---

### Post by linuchsan on 2006-07-11
Can you post your smb.conf?

---

### Post by Dearhell on 2006-07-11
I think my samba configuration it's all right, because as I said, I can access to the shared folder without any problem from windows.

Anyway, here it is:

> [public]
        comment = Public Folder
        path = /home/admin/public
        force user = nobody
        force group = nogroup
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes


In the rest of the smb.conf configuration, I have only change security = user by security = share, but I can post it anyway if it helps

---

### Post by Dearhell on 2006-07-11
May be it only can be mounted with security = user?

---

### Post by Dearhell on 2006-07-12
Bumping :roll:

---

### Post by tturrisi on 2006-07-12
[http://ubuntuguide.org/wiki/Dapper#Networking](http://ubuntuguide.org/wiki/Dapper#Networking)

---

### Post by Dearhell on 2006-07-12
I have read that before post, but it didn't help

---

### Post by spafbnerf on 2006-07-14
having the exact same problem. :(

smb_fill_super: missing data argument

i installed a dapper drake release candidate and upgraded it... u?

i've since upgraded to the latest available kernel & version of samba in the repo hoping it would fix this, no such luck.

ii  libsmbclient   3.0.22-1ubuntu
ii  samba          3.0.22-1ubuntu
ii  samba-common   3.0.22-1ubuntu
ii  smbclient      3.0.22-1ubuntu
ii  linux-image-2. 2.6.15-26.44

---

### Post by linuxkitten on 2006-07-16
](*,) 

I as well have the same problem.  I recently updated from Fedora Core 4 to 5.  In 4 the mount worked perfectly, but once updated...

Using Konqueror   'smb://host_name/share_name'   will allow you to read and write to them.  Nautilus will also do the same.

But this is a hassle when I go to burn somthing off the share, k3b wont access it unless its mounted.  So I'm forced to copy it locally first.

best of luck,
LinuxKitten

---

### Post by Thund3rstruck on 2006-07-16
Sorry guys it took so long to reply back on this one. 

Yea, you have to install smbfs first. CIFS and smbfs is not installed by deafault with Ubuntu and it's different from samba. Samba is for sharing files and smbfs/cifs is for reading the cifs/smb filesystem

```

sudo aptitude install -y smbfs

```

or subustitute aptitude for apt-get if you prefer

---

### Post by linuxkitten on 2006-07-16
Well I just got it figured out on my setup.(with some searching on cifs)

on the client you need the samba-client package installed.

on the host in samba.conf, you need:
security=share

The command:
mount -t cifs //Host_Name/Share_Name Mount_point -o guest
will then mount the share.
:-D

---

### Post by Dearhell on 2006-07-18
> **Thund3rstruck said:**
> Sorry guys it took so long to reply back on this one. 

Yea, you have to install smbfs first. CIFS and smbfs is not installed by deafault with Ubuntu and it's different from samba. Samba is for sharing files and smbfs/cifs is for reading the cifs/smb filesystem

```

sudo aptitude install -y smbfs

```

or subustitute aptitude for apt-get if you prefer

I had installed smbfs when I posted

---

### Post by Dearhell on 2006-07-18
> **linuxkitten said:**
> Well I just got it figured out on my setup.(with some searching on cifs)

on the client you need the samba-client package installed.

on the host in samba.conf, you need:
security=share

The command:
mount -t cifs //Host_Name/Share_Name Mount_point -o guest
will then mount the share.
:-D

I don't see in that command where do you specify the folder where it will be mounted

I have tried this:

> mount -t cifs //192.168.1.5/public laptop/ -o guest

But dmesg | tail displays these errors:

> [17180654.708000] Buffer I/O error on device fd0, logical block 0
[17180654.772000] end_request: I/O error, dev fd0, sector 0
[17180654.772000] floppy0: disk absent or changed during operation
[17180654.772000] end_request: I/O error, dev fd0, sector 0
[17180654.772000] Buffer I/O error on device fd0, logical block 0
[17180705.056000] /dev/vmmon[5112]: host clock rate change request 83 -> 1043
[17182083.200000] /dev/vmmon[5112]: host clock rate change request 1043 -> 83
[17182089.796000] /dev/vmmon[5112]: host clock rate change request 83 -> 1043
[17192950.260000]  CIFS VFS: No username specified
[17192950.260000]  CIFS VFS: cifs_mount failed w/return code = -22


---

### Post by linuxkitten on 2006-07-18
mount -t cifs //Host_Name/Share_Name */Mount_path/Mount_directory* -o guest

Example:
mount the share *'public'* on local folder *'/mnt/nfs'*
   mount -t cifs //192.168.1.5/public /mnt/nfs -o guest

You may be having a problem due to your configuration file.
I was not able to mount the share with the variable "guest account" set.

Here is a concise smb.conf that I have successfully tested on my Xbox:
#------------------------
[global]
   workgroup = WORKGROUP
   server string = Xbox
   log file = /var/log/samba/%m.log
   max log size = 50
#   guest account = nobody
   security = share
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   dns proxy = no 

#Share Definitions
   idmap uid = 16777216-33554431
   idmap gid = 16777216-33554431
   template shell = /bin/false
   winbind use default domain = no

[public]
  comment = Public Folder
  path = /home/public
  force user = nobody
  force group = nobody
  read only = No
  create mask = 0744
  directory mask = 0777
  guest ok = Yes
#------------------------
It allows me to write and delete files.

if you need further help I'm avaible at
AIM: LinuxKitten
Yahoo IM: LnxKitten

---

### Post by msandersen on 2006-07-18
I seem to remember having read that you cannot have spaces in your Samba share name, ie it only sees the share "public" not "public laptop". The error is saying that "//192.168.1.6/public" is wrong, which it is. Change the share name on Windows to Public-Laptop or simply Public, and I think your problem will go away. You could try the mount command with the path in quotes, but I don't think that'll work, at least it won't in an fstab. Maybe it will by the mount command. I'm on Windows right now, so can't check.
In any case, you're better off avoiding spaces in your Windows shares.

---

