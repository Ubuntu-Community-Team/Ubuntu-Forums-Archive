---
title: "'mail' utility error"
date: 2009-02-12
forum: General Help
---

### Post by Ugluk on 2009-02-12
When I'm using 'mail' program, I'm getting following error:
mail: /var/mail/myname : File or directory doesn't exist.
If I create this file manually, there is Permissions error, despite this file is 'rw' both for user and 'mail' group.
How I can fix it?

---

### Post by spiderbatdad on 2009-02-12
You should not have to specifically create a folder. Mail to your username should appear in the folder /var/mail and be readable by you. You may get a mail to "mail" also. For example a message from the system. This would be owned by mail:mail and require root permission to read.

You can use your terminal and navigate to /var/mail```
cd /var/mail
```
Now run ```
ls -l
```to see the messages and what user:group the mail belongs to. ```
sudo cat filename
```where filename is the name of some file in the folder /var/mail should allow you to read any of those files.

---

### Post by e1mer on 2009-02-12
It may be that the path is not present either.

Usually mail goes in /var/spool/mail, not /var/mail.

Please type the following two commands:
```
 
ls -ld /var/spool/mail 
ls -ld /var/spool/mail 

```
and let us know what the result it.

---

### Post by Ugluk on 2009-02-12
```
$ sudo ls -l /var/mail
-rwxrw-rw- 1 myname mail 0 2009-02-10 01:43 myname

$ ls -ld /var/spool/mail
lrwxrwxrwx 1 root root 7 2009-02-03 01:27 /var/spool/mail -> ../mail
```

---

### Post by spiderbatdad on 2009-02-12
that shows you the folder mail in /var/spool/mail is just a symbolic link to /var/mail. This is correct.
Are you still having trouble? Please describe what steps you take to send mail and/or read mail.

---

### Post by Ugluk on 2009-02-12
Using mail for testing like:
```
mail -s Test myname
test
.
```
has no indication of success or failure.
Trying to read it by just 'mail':
```
mail: /var/mail/myname: Permission denied
```
This file exist and is 0 bytes. Despite I am it's owner and have at least read access, I cannot even cat it content.

---

### Post by dcstar on 2009-02-12
> **Ugluk said:**
> Using mail for testing like:
```
mail -s Test myname
test
.
```
has no indication of success or failure.
Trying to read it by just 'mail':
```
mail: /var/mail/myname: Permission denied
```
This file exist and is 0 bytes. Despite I am it's owner and have at least read access, I cannot even cat it content.

Do you have the **mailx** package installed?, if so try a reinstall.

---

### Post by spiderbatdad on 2009-02-12
try your session like this:

```
mail ugluk
#this should produce a subject line
Subject:
# type subject and hit enter, or just hit enter
#return empty line. Type message...
ctrl+d to Cc:
ctrl+d to quit

#now read mail
mail
1
 q to quit
ctrl+d to exit
```

---

### Post by Ugluk on 2009-02-12
I have reinstalled mailx package.
Sending part works without errors, but reading fails with aforementioned Permission error. Moreover, I have added a user, and he gets the same error. His mailbox isn't even being created in /var/mail.
Here's permissions for /var/mail:
drw-rwSrwT 2 root mail 4096 2009-02-10 01:43 /var/mail

---

### Post by dcstar on 2009-02-12
> **Ugluk said:**
> I have reinstalled mailx package.
Sending part works without errors, but reading fails with aforementioned Permission error. Moreover, I have added a user, and he gets the same error. His mailbox isn't even being created in /var/mail.
Here's permissions for /var/mail:
drw-rwSrwT 2 root mail 4096 2009-02-10 01:43 /var/mail

Here is mine:

```
drwxrwsr-x  2 root mail  4096 2009-02-13 15:02 mail
```

---

### Post by Ugluk on 2009-02-13
Adding 'execute for all' to /var/mail seems to solve the problem.

---

