---
title: "htpasswd issue"
date: 2009-04-29
forum: General Help
---

### Post by Manasia on 2009-04-29
Hello Folks!

When I run the htpasswd I get the following:

root@Addison:/etc/apache2/passwords#
**> htpasswd -c -s .htpasswd demo medsphere** (Command I ran)
Usage:
        htpasswd [-cmdpsD] passwordfile username
        htpasswd -b[cmdpsD] passwordfile username password

        htpasswd -n[mdps] username
        htpasswd -nb[mdps] username password
 -c  Create a new file.
 -n  Don't update file; display results on stdout.
 -m  Force MD5 encryption of the password.
 -d  Force CRYPT encryption of the password (default).
 -p  Do not encrypt the password (plaintext).
 -s  Force SHA encryption of the password.
 -b  Use the password from the command line rather than prompting for it.
 -D  Delete the specified user.
On Windows, NetWare and TPF systems the '-m' flag is used by default.
On all other systems, the '-p' flag will probably not work.

It never creates the file, this is all it does. Anyone know what I am doing wrong? When I try -cs I get the same thing as well.

---

### Post by Kareeser on 2009-04-29
Simplify at first, try without the s switch...

Are demo and medsphere two users, or a user and a password? Looks like you might need the "b" switch if medsphere is the password.

---

### Post by Manasia on 2009-04-29
Dude your a GENUIS!

I guess you have to create the standard file first and then add your hashing type afterwards.

Thanks a lot man.

---

### Post by Kareeser on 2009-04-29
Hehe, thanks.

htpassword is a confusing utility to use at first. I spent a lot of time scratching my head at the beginning.

It's always good to simplify and try to progrssively more complex commands, so you know which switch you're using incorrectly.

---

### Post by Manasia on 2009-04-29
Point every well taken.

---

