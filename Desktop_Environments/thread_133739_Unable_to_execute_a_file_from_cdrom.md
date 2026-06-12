---
title: "Unable to execute a file from cdrom"
date: 2006-02-20
forum: Desktop Environments
---

### Post by samba on 2006-02-20
Hi,

I'm trying to install Mathematica from a cdrom, but i can't execute the installer file. It says

```

sudo: unable to execute ./MathInstaller: Permission denied

```

I've tried various things, like using "sh" instead of "./", and also copying the installer file on my harddisk and running it from there, but in these two cases it doesn't work and says

```

Your system type cannot be determined.
You are in the wrong directory to run MathInstaller.
Try again following these instructions:
cd /cdrom/Unix/Installers/<\SystemID>
./MathInstaller

```

I don't know what to do! It used to work on Hoary. Here's my cdrom line in the /etc/fstab file:

```

/dev/hdb        /media/cdrom0   udf,iso9660 exec,ro,user,noauto     0       0

```

"exec" is there, so it should work, no?

Thanks a lot for your help,
Samba

---

### Post by larsemil on 2006-02-20
u did a: 
sudo sh mathinstaller

sh runs the file even though the permissions are not set.

---

### Post by samba on 2006-02-20
[QUOTE=larsemil]u did a: 
sudo sh mathinstaller

sh runs the file even though the permissions are not set.[/QUOTE]

Yes exactly, but it gave me the error message above...

ciao :-)
vincent

---

### Post by larsemil on 2006-02-20
it could be that something about sudo fucks it up. i installed something(dont remember) the other day and had to log in as root to install it.

try a sudo su -

and then install. otherwise i have no idea.

---

### Post by samba on 2006-02-20
[QUOTE=larsemil]
try a sudo su -

and then install[/QUOTE]

Hmm I've tried that as well but it doesn't solve the problem... Thanks for your help anyway! Anyone else has any other ideas?

Thanks,
Vincent

---

### Post by samba on 2006-05-17
Hello people,

I'm now using Dapper Beta, on a new laptop, trying again to install Mathematica, and I get exactly the same error messages as in my first post... This is getting very annoying! I really don't know what to do to execute a file from the install cdrom.

Any ideas???

thanks :-)
vincent

---

