---
title: "File sharing WITH a password"
date: 2010-04-19
forum: Desktop Environments
---

### Post by abean on 2010-04-19
Hi there,

I recently installed ubuntu 9.10, and upgraded all packages (yesterday actually).

After sharing a folder it worked without a hitch, but I wanted to add a username and password. I've added an smb user but it doesn't seem to work. 
The only think i can do is tick/untick a box that lets other users read/write files. 

I've searched the forum but I can't find anything on this, its the other way round of trying to get rid of the password lol

---

### Post by micio on 2010-04-19
in smb.conf you must ensure that:

```
security = user 
```

and it could be a good idea that for each share you use

```
valid users = your smb users
```

if the problem persist please post here your smb.conf file

---

### Post by Morbius1 on 2010-04-19
Perhaps there is a conflict between Nautilus-share and Classic-share. Post the output of the following commands so we can see what method of sharing you are using and how your shares are set up:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

---

### Post by abean on 2010-04-20
$>net usershare info
[data]
path=/home/dcmcompliance/Data
comment=
usershare_acl=Everyone:F,
guest_ok=n


$>testparm -s
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

---

### Post by abean on 2010-04-20
I have added a user already, with the same name as the default user account. 

I also changed the smb.conf already to security = user but that didn't help.

---

### Post by Morbius1 on 2010-04-20
> After sharing a folder it worked without a hitch, but I wanted to add a username and password. I've added an smb user but it doesn't seem to work.When you say it doesn't work, do you mean it grants you access without an authentication prompt?
>          I have added a user already, with the same name as the default user account. Just so I understand, is the remote user accessing the Ubuntu share using the Ubuntu users username and password?

And is the remote user Windows?
And does the Windows login username and password match the Ubuntu samba username and password?

There's a design flaw in how Windows browses the network. Along with the request to view available shares it will actually pass it's local Windows login username and password. If it matches the samba username and password then no authentication is required because it's already been supplied.

If you change the samba password for that remote user to something other than their login password you should get a prompt.

---

### Post by abean on 2010-04-20
> When you say it doesn't work, do you mean it grants you access without  an authentication prompt?

You can access the shared folder without any authentication

> And is the remote user Windows?
Yes, and you do not need to enter any username/password information

login/username on windows does not match the ubuntu username and passwod

smb username is the same as ubuntu username. Windows is different to both of these.

---

### Post by Morbius1 on 2010-04-20
The only thing I can think of at the moment is another flaw in Windows SMB. If windows ever successfully connects with the correct credentials it will remember it forever and pass those credentials to the server automatically.

There's a way to fix that on Windows but try an experiment:

Change the smb password on the linux box to something different that what it is right now.
Restart the samba service
Try to connect from Windows and see if you get prompted for a username and password.

---

### Post by abean on 2010-04-21
Do you have the exact commands for that? Just to avoid confusion and I'm not adding users by accident....

I did reboot the Windows machine, which I think makes it forget about the connection. 

I appreciate all this help btw  :biggrin:

---

### Post by Morbius1 on 2010-04-21
Windows doesn't forget after a reboot. The only way on Windows to stop that behaviour is by a enabling the "Network access: Do not allow storage of credentials or .NET Passports for network authentication" feature in the "Local Security Policy" management console.

Rather than fool with Windows' internals I would just reset the samba password:

Let's say your username is morbius,

Open **Terminal**
Type **sudo smbpasswd morbius**

It will first ask you for the sudo password
Then it will ask you for the new samba password.

[COLOR=Blue]EDIT:[/COLOR] Actually, I don't think you need the sudo part since ( in this example ) morbius is changing his own password. But it doesn't matter  either way - sudo or no sudo

---

### Post by abean on 2010-04-22
Turns out it was the windows bug I think. For some reason you now need a password.

Thanks for all the help guys!

---

