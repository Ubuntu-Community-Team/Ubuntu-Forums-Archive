---
title: "Openssh 5.1 sftp chroot and file permissions (umask)"
date: 2009-03-27
forum: General Help
---

### Post by fozzyuw on 2009-03-27
I have Openssh 5.1 for sftp with chroot enabled that jails account to their home directory.  The file structure is setup like this...

/home/sftp/[business division]/[customer name]/files/[...]

There's a master ftp accounts set for their respective business divisions (marketing, engineers, etc) and a customer account that's home directory is set to the "customer name" directory.

This allows the master account, sftpadmin, to see all the customer account directories but jails the customer into only seeing their directory.

All directories are owned and writable only by root, as required by Openssh chroot, up to files.  The "files" directory owner is set to the customers account, while the group is set to "sftp" which the "sftpadmin" is a part of.

Everything works well up to this problem; Openssh always sets the file permissions to "RW-R--R--" regardless of what "umask" is set as.

This is a problem because if a customer uploads a file, the admin cannot delete it because they do not have write permissions to do so because their group does not have write permissions.

On a second problem, I noticed that the customer account can chmod the files and folders in their account.  Is there a way to lock them out from this?  I've already made their shell "/bin/false".

Thanks!
Fozzy

---

### Post by fozzyuw on 2009-03-31
Hmm..

A couple more days and still no luck trying to figure this out.  I've tried to use rssh but kept running into issues getting that running.

From what it seems, there's two possibilities:

a) Copying a file from a Windows machine to the Linux server, via WinSCP, gives the files permissions nothing more than "RW-R--R--", thus, no matter what the mask is, the file doesn't ever has the permissions to begin with.

I tried setting a file with full permissions (777), then copying it to the Windows machine and back, only to have the it reset to 644.  This could simply mean the file doesn't preserve the permissions across non-like systems (Windows/Linux).  Which would mean, when copying from Windows back to Linux, something has to set the permissions to something and it's either WinSCP or Linux.

Can anyone confirm how files obtain their permissions when copying from one server to another?  Are the file permissions reset to (777) and then the system umasks them based on their setup?

b) The second possibility I see is that even though I'm logged in as a specific user, it pulls the roots default umask.  I noticed that anytime I do "sudo touch myfile.txt" I get the same file permission set; "RW-R--R--".  So, it makes me wonder if the OpenSSH process isn't switching to be the root to copy the file?

C) I suppose a third possibility is that OpenSSH is just hard coded to make file permissions "RW-R--R--" for files?  I saw someone with a modified OpenSSH that allowed sftp-internal to accept parameters for setting a umask.

Anyone else seem to have this issue?

I've tried setting umask in the directory.
I've tried setting umask in /etc/profile (but as I understand it Bash doesn't even read from this when logged in via WinSCP).
I've tried setting the umask in /etc/init.d/ssh

Unfortunately, no luck with any of that.

I find it bizarre that it's so difficult or complicated to just setup a secure FTP server for individual users and a super (admin) user.

---

### Post by fozzyuw on 2009-04-02
To continue to try and troubleshoot this issue, does anyone know why I'm having this issue:

```
fozzy@file-serv:/home/sftp/files$ ls -l
-rw-r--r-- 1 root    sftponly 0 2009-04-02 14:39 file1.txt
fozzy@file-serv:/home/sftp/files$ umask
0022
fozzy@file-serv:/home/sftp/files$ umask 077
fozzy@file-serv:/home/sftp/files$ umask
0077
fozzy@file-serv:/home/sftp/files$ sudo touch file2.txt
fozzy@file-serv:/home/sftp/files$ ls -l
-rw-r--r-- 1 root    sftponly 0 2009-04-02 14:39 file1.txt
-rw-r--r-- 1 root    sftponly 0 2009-04-02 14:39 file2.txt

```

I then tried to edit /etc/profile
```
fozzy@file-serv:/home/sftp/files$ sudo vim /etc/profile
----
#umask 022
umask 077
:wq
----
fozzy@file-serv:/home/sftp/files$sudo reboot

^^^^^ login ^^^^^

fozzy@file-serv:~$ cd /home/sftp/files
fozzy@file-serv:/home/sftp/files$ umask
0077
fozzy@file-serv:/home/sftp/files$ sudo touch file3.txt
fozzy@file-serv:/home/sftp/files$ ls -l
-rw-r--r-- 1 root    sftponly 0 2009-04-02 14:39 file1.txt
-rw-r--r-- 1 root    sftponly 0 2009-04-02 14:39 file2.txt
-rw-r--r-- 1 root    sftponly 0 2009-04-02 14:39 file3.txt

```
I'm not following why I'm still not getting the umask being set via touch.  I'm assuming the newly created file should be "-rw-------".

Any thoughts as to this step?  I'm guessing this might be part of the issues I'm experiencing.  I'm also looking into setting pam_umask to see if that will work.

Fozzy

---

### Post by bfisk@seegrid.com on 2010-04-21
Where you able to figure out how to do chroot and also setting umask for group permissions?

---

### Post by tannerb on 2010-06-24
I had a similar problem recently. I wanted my openssh sftponly-style users to create files user and group writable, but I wanted my ssh login users to create files only user writable. I solved it thusly:

    In my /etc/ssh/sshd_config, I have:
 ```
Match user my,user,list
    ForceCommand internal-sftp 
    ChrootDirectory /some/dir/  
```In /etc/pam.d/sshd I added:
```
 session    optional pam_umask.so umask=0002
```Than in /etc/profile I added:
```
  umask 022
```Using internal-sftp means that there aren't any shells being executed, which means the profile/login/rc stuff never gets executed. pam_umask.so however gets hit during authentication. 

 There's probably a slightly more delicate way to handle who gets what umask than starting with a pam_umask then overriding it in all of the shells but it's working for my case. Hope it saves someone else the hour I spent looking at every available method of setting umask.

---

### Post by j_b_poquelin on 2010-07-21
> **tannerb said:**
> I had a similar problem recently. I wanted my openssh sftponly-style users to create files user and group writable, but I wanted my ssh login users to create files only user writable. I solved it thusly:

    In my /etc/ssh/sshd_config, I have:
 ```
Match user my,user,list
    ForceCommand internal-sftp 
    ChrootDirectory /some/dir/  
```In /etc/pam.d/sshd I added:
```
 session    optional pam_umask.so umask=0002
```Than in /etc/profile I added:
```
  umask 022
```Using internal-sftp means that there aren't any shells being executed, which means the profile/login/rc stuff never gets executed. pam_umask.so however gets hit during authentication. 

 There's probably a slightly more delicate way to handle who gets what umask than starting with a pam_umask then overriding it in all of the shells but it's working for my case. Hope it saves someone else the hour I spent looking at every available method of setting umask.

Wow, thank you so much ! I was getting nut with the same problem... Great solution !

---

### Post by 314ttus on 2011-01-12
Hi tannerb,

I had the same kind of problem. Great solution. Thank you very much!

Peter

BTW: Older ubuntu versions (like 7.10) name the file '/etc/pam.d/ssh'

---

### Post by Rob_H on 2011-12-10
This was very helpful to me as well. Did you figure out how to prevent jailed users from invoking chmod?

---

