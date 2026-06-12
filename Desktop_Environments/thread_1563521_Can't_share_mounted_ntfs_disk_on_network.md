---
title: "Can't share mounted ntfs disk on network"
date: 2010-08-29
forum: Desktop Environments
---

### Post by VanillaMozilla on 2010-08-29
I have samba installed.  I also have a Windows NTFS disk mounted on Ubuntu.  To share the file, I migrate to the folder with the file manager, right click on it and select "Sharing Options".  I get the message

'net usershare' returned error 255:  net usershare add:
cannot share path /mnt/Windisk/<path> as we are restricted to only sharing directories we own.  Ask the administrator to add the line "usershare owner only = false" to the [global] section of the smb.conf to allow this.


The disk is mounted by the system with the line 

/dev/sda2 /mnt/Windisk ntfs-3g defaults 0 0
in fstab.


Here's what I've tried:
=========================
Adding the line to fstab and rebooting does not solve the problem.  I still get error 255, but without the advice.

Changing ownership does not help.  I tried
sudo chown -v root:sambashare /mnt/Windisk/<path>
and
sudo chown -v mylogin:sambashare /mnt/Windisk/<path>
changed ownership of `/mnt/Windisk/<path>' to mylogin:sambashare

Chown confirms the change, but right clicking on file, Properties tab still shows root owns file, and I still get an error 255.

---

### Post by Morbius1 on 2010-08-29
> 'net usershare' returned error 255:  net usershare add:
cannot share path /mnt/Windisk/<path> as we are restricted to only  sharing directories we own.  Ask the administrator to add the line  "usershare owner only = false" to the [global] section of the smb.conf  to allow this.There's two ways to fix this, one of which is offered in what is probably the best written error message in all of computing :D

When you added:
```
usershare owner only = false
```Did you do it without quotes?
And did you save smb.conf and restart the samba daemon:
```
sudo service smbd restart
```

---

### Post by VanillaMozilla on 2010-08-29
Yes, I added it without quotes, and I ran testparm to make sure the line worked.  I rebooted the computer, so there is no question that samba restarted.  I still got error 255, but this time I got it without the advice to add that line to the file.


EDIT:  It turns out that it doesn't work unless the share name is the same as the directory name.

But there's another problem.  I can't view it on the Ubuntu client.  It's asking for a password AND a domain name.  There should be no password and there is no domain -- it's workgroup WORKGROUP.  The form keeps filling in domain "MSHOME".  I have all the passwords and it doesn't work with any of them.

Checking the box "Allow others to create and delete files in this folder" makes no difference.

---

### Post by Morbius1 on 2010-08-30
Post the output of these 3 commands please:
```
net usershare info
``````
sudo net usershare info
``````
testparm -s
```

---

### Post by VanillaMozilla on 2010-08-30
Interesting.  Something is going on here, for sure.  By way of explanation, I tried to name the share "thunderprof", but I had to mount it as "profiles".  ls -Fal shows I am the owner of "profiles", but root is the owner of "thunderprof".


:~$ net usershare info
[profiles]
path=/mnt/Windisk/DocumentsAndSettings/Common/ApplicationData/Thunderbird/Profiles
comment=
usershare_acl=Everyone:R,
guest_ok=n



:~$ sudo net usershare info
info_fn: file /var/lib/samba/usershares/thunderprof is not a well formed usershare file.
info_fn: Error was Path is not a directory.


:~$ testparm -s
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
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d

<printer sections omitted for brevity>

---

### Post by Morbius1 on 2010-08-30
> :~$ [COLOR=Blue]net usershare info[/COLOR]
[profiles]
path=/mnt/Windisk/DocumentsAndSettings/Common/ApplicationData/Thunderbird/Profiles
comment=
usershare_acl=Everyone:R,
[COLOR=Blue]**guest_ok=n**[/COLOR]

:~$ [COLOR=Blue]sudo net usershare info[/COLOR]
info_fn: file /var/lib/samba/usershares/thunderprof is not a well formed usershare file.
info_fn: Error was Path is not a directory.
> I tried to name the share "thunderprof", but I had to mount it as "profiles"**(1)** You did a "gksu nautilus" somewhere along the line and creates a Nautilus-share for "thunderprof". Then you created another one under your own username.

I would go back in as gksu nautilus and remove the thunderprof share to clear this up.

(2) The reason the client is asking for authentication is because you have the share set to not allow guests. Go back into nautilus and check the "allow guests" option.

---

### Post by VanillaMozilla on 2010-08-30
> **Morbius1 said:**
> **(1)** You did a "gksu nautilus" somewhere along the line and creates a Nautilus-share for "thunderprof". Then you created another one under your own username.

I would go back in as gksu nautilus and remove the thunderprof share to clear this up.
Yikes!  Nonorthogonal tools and paths to be undone.

Yes, that's correct, I did run gksudo nautilus.  But now I can't find the share.  The mount point doesn't show any sharing, and I can't get to the actual ntfs disk (only the mount point).  Also, Nautilus won't show me the path in text form when I start it from gksudo!  gksudo shares-admin shows no shares (I do have "profiles" turned off).  Is there a file I can edit?



> **Morbius1 said:**
> (2) The reason the client is asking for authentication is because you have the share set to not allow guests. Go back into nautilus and check the "allow guests" option.
OK, that seems to work.

But how am I going to clean up thunderprof?

---

### Post by VanillaMozilla on 2010-08-30
Oh, wait, I see the problem.  thunderprof refers to a mount point that has been changed.  It was on /media, now it's on /mnt.

Stand by....

---

### Post by VanillaMozilla on 2010-08-30
Note to self (and anyone else who enjoys masochism) :)

OK, this is defying a fix for now, and I'm out of time.  I tried just renaming thunderprof and the system just used the renamed file!

I'm afraid to delete it outright, for fear of breaking something else.  It's write protected.

And just changing the mount point and rebooting failed (user error?).  I don't know.  I'll try later.

---

### Post by Morbius1 on 2010-08-30
Your making this too complicated. Let's try a different path.

Nautilus-shares creates share definitions at the following location:
> /var/lib/samba/usersharesOpen nautilus as root:
```
gksu nautilus
```And go to /var/lib/samba/usershares

Once you're there you should see 2 files:
> profiles
thunderprofIf you doulble click on thunerprof you will see something like this:
> #VERSION 2
path=/media/Windisk/DocumentsAndSettings/Common/ApplicationData/Thunderbird/Profiles
comment=
usershare_acl=S-1-1-0:F
guest_ok=yIt's just a config file that tells samba what to do with the folder. Just delete the file - it's not deleting the source.

---

### Post by VanillaMozilla on 2010-08-30
OK, that worked.  (Actually, I wasn't making it so complicated.  I just needed to move it out of the directory or delete it instead of renaming it.)

Thanks very much for all your accurate diagnosis.


*************************
EDIT:  Darn.  There's yet another problem.  The client doesn't recognize the share from a command line.  This is going in circles.  I'll work on it maybe tomorrow evening and see if I can either solve it or define the problem better.

---

### Post by VanillaMozilla on 2010-08-31
OK, here's the big problem.

thunderprof is shared, but I can't read it from the mount point on the client computer.
ls /mnt/thunderprof shows no files.
Nautilus shows no files in /mnt/thunderprof , but shows the files in smb://computername/thunderprof

mount -a gives error message:
mount error: could not resolve address for <computername>:  No address associated with host name
No ip address specified and hostname not found.


Any ideas?  I thought I had this solved once.  I need command-line access for the Thunderbird configuration file "profiles.ini".


/etc/fstab has the line
//computername/thunderprof /mnt/thunderprof cifs guest,uid=1000,iocharset=utf8, codepage=cp850 0 0

---

