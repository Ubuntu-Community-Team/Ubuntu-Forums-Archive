---
title: "[SOLVED] Windows XP cannot write to shared Samba Drive"
date: 2008-12-09
forum: Desktop Environments
---

### Post by msboston01 on 2008-12-09
Hello folks,

The deal is simple, yet, I can't fix it. I have a pretty big Ubuntu 8.10 PC with 6 drives, 5 of which are shared with SAMBA / SWAT.

I created in Ubuntu a user called sambauser, then created the samba account with a password using the utility smbpasswd and created a smbusers file with the correspondance sambauser = "sambauser". So far so good, everyone is happy. 

I set my user sambauser in SWAT so it can read AND write to any drive (global parameter)

```
[global]
	workgroup = WORKGROUP
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	ldap ssl = no
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	valid users = sambauser
	admin users = 
	read list = sambauser, nobody
	write list = sambauser

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[/media/DiskB-500/VideoStore1]
	available = No

[/media/DiskA-250/Musicstore1]
	available = No

[/media/DiskF-80/Picturestore1]
	available = No

[/media/DiskE-80/DVDStore2]
	available = No

[/media/DiskD-400/DVDStore1]
	available = No

```

Then I go on my Windows XP, map a drive to say DVDStore1, using the "connect using a different user name" where I enter sambauser with the password. I open the mapped drive and I can read all the contents, except I cannot write anything because "Access is denied".

Help!

---

### Post by DieB on 2008-12-10
did u set the read-write permissions correct on your linux?

sudo chmod -R 777 [path]

would do that on commandline

ps: more here:

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html#permissions](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html#permissions)

---

### Post by msboston01 on 2008-12-10
Additional information:

- Samba takes the sambauser login and password when mapping the drive. If I put the wrong password for example, it kicks me out so it is safe to say that the password verification routine works.

- I have a feeling that anyone can access as read only, even if I disable the guest account, as if the policy was set to SHARE instead of USER as it is now. As a matter of fact, when I switch the policy to SHARE, it's just the same thing... anyone can read, no one can write.

- I have rebooted the SMB daemons over and over again using sudo /etc/init.d/samba restart

- Maybe I need to specify the path for users somewhere but I don't know where to do that...

Any help would be greately appreciated. I don't know what to do at this point. Thanks

Nic

---

### Post by msboston01 on 2008-12-10
Dieb,

I have given permission to SAMBA, but not for every individual shared drives. Is that what you are suggesting?

For example, should I run the following?
sudo chmod -R 777 /media/DiskF-80/Picturestore1

Thanks

---

### Post by DieB on 2008-12-10
well somehow yes, cause sambauser or the winuser need to have permission to write and read on the data.

me had a lot of problems with the linux file restrictions while i set up mine network. so it would be good to have either sambauser be the owner of the files or add sambauser to the group of the owner - then 770, or better 660 might work.

pls use 6 (read,write) instead of 7 (read,write,execute) ;)

---

### Post by msboston01 on 2008-12-10
I agree.

This file restriction strategy has been at the source of all the issues I had with Ubuntu. Maybe one day that will be eased up with a nice utility instead of complicated command lines.

Until then, we've got what we've got :)

Ok, it looks like I need to give read/write to SAMBA to all my mounted shares. Should this be an entry in the FSTAB file?

---

### Post by DieB on 2008-12-10
hi,

well it might be the source of problems, but it is also a prevention of problems ;)

fstab might make sense (there are the gid and uid flags with which u can set the owner of that partition) but the command from above typed six times ain't that hard either.

to make smabauser the owner, type:

sudo chown sambauser:sambauser -R [directory]

---

### Post by msboston01 on 2008-12-10
Nope :(

```
sudo chmod -R 660 /media/DiskE-80
```

That didn't do the trick. Shouldn't SWAT be the owner of these shares? Or at least the account that I use to manage SWAT? I think that this is the real problem.. that SWAT does not have these permissions...

I tried adding entries to the FSTAB but that didn't work too (drives won't mount for some reason).

I am using the DiskE-80 to make all my changes because it is empty so if something goes terribly wrong, I won't loose data.

Any suggestions?

---

### Post by DieB on 2008-12-10
well swat is the program, but as far as i understood swat (a netinterface to samba) passes on the loginuser.

so it should work with sambauser.

sudo chown samabauser:sambauser - R /media/DiskE-80/DVDStore2

---

### Post by msboston01 on 2008-12-10
Didn't work either... 

```
sudo chown samabauser:sambauser - R /media/DiskE-80/DVDStore2
```

So when I VNC in the server, I can modify, create, delete files using sambauser. Yet, when I access it through Samba, I can't. Could my mapping be inaccurate somehow? 

Here's what I have in my /etc/samba/smbusers file:

```
sambauser = "sambauser"
```

I have added since yesterday the following line in my smb.conf file:

```
username map = /etc/samba/smbusers
```

Didn't work either but it was worth a try...

---

### Post by DieB on 2008-12-10
what is the "avaibale = no" in your samba config for?

pls try it with:

path = /path/to/share/point
        browseable = yes
        writeable = yes


sorry, i oversaw that in the beginning

---

### Post by msboston01 on 2008-12-10
mm I think we are on to something.

I tried to make the changes in the smb.conf you are suggesting, but apparently, SWAT gets rid of them and reverts the entries back to Available = No...

It may be a SWAT problem after all...

---

### Post by msboston01 on 2008-12-10
Well well well... additional information...

The shares that I am seeing ARE NOT SAMBA SHARES. I decided to delete all these shares one by one, and they are still here!

I think they come from the previous shares that I had set up with Nautilus (right click on folder, sharing options) before installing SWAT. 

Now how can I terminate these?

---

### Post by msboston01 on 2008-12-10
ok, I managed to get rid of everything... I also re-created my shares and I guess I am back to square 1 with read only everywhere.

Anyone with an idea?

---

### Post by msboston01 on 2008-12-10
VICTORY IS MIIIIIIIIIIIIIIIIINE

removed the mapping to smbuser file, recycled the services and I can write!!!!!!!!!!!!

This resolution doesn't really make sense but hey, it floats my boat. :guitar:

---

### Post by DieB on 2008-12-11
great to hear.

u definitly have to make an safe backup of that config, cause in a half a year u might not remember.

---

