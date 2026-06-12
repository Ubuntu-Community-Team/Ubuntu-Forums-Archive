---
title: "files and permissions"
date: 2009-05-26
forum: General Help
---

### Post by lex1 on 2009-05-26
I have cgi-bin and cgi-data in /www/var/ they have to be moved to /var/www/modified cgi-data has to be owned by webserver(www-data) cgi-bin owned by root but readable webserver www-data

how can this be accomplished

lex1

---

### Post by geirha on 2009-05-26
Are you asking how to change ownership and permissions on files? This page explains permissions and ownership [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by lex1 on 2009-05-26
yes i have seen this but I am dyslectic and cannot follow
but thankyou for replying

lex1:popcorn:

---

### Post by Boondoklife on 2009-05-26
> **lex1 said:**
> I have cgi-bin and cgi-data in /www/var/ they have to be moved to /var/www/modified cgi-data has to be owned by webserver(www-data) cgi-bin owned by root but readable webserver www-data

how can this be accomplished

lex1


Just check out chown and chmod that is all ya need

owned by root readable by www-data
```
chown root:www-data cgi-bin
chmod 750 cgi-bin
```tack a -R on the end of it if you want to change all the files in the folder to the same things too.

---

### Post by geirha on 2009-05-26
I see, well I could provide you the commands to do it, but it's best to know the current permissions and ownership first. The following two commands should show the different permissions and ownership of files under cgi-bin and cgi-data:

```
sudo find /var/www/modified/cgi-bin -printf "%M %u %g\n" | sort -u
sudo find /var/www/modified/cgi-data -printf "%M %u %g\n" | sort -u

```

---

### Post by lex1 on 2009-05-26
here is what is right now

my /var/www is below

total 32
drwxr-xr-x  5 root root 4096 2009-05-26 09:20 .
drwxr-xr-x 15 root root 4096 2009-02-27 21:05 ..
drwxr-xr-x  2 root root 4096 2009-05-20 11:47 cgi-bin
drwxr-xr-x  3 root root 4096 2009-05-26 09:13 cgi-data
-rw-r--r--  1 root root  940 2009-04-17 16:08 gpf_pto2.css
-rw-r--r--  1 root root 6003 2009-03-07 17:10 index.html
drwxr-xr-x  4 root root 4096 2009-03-09 19:46 modified


inside cgi-bin there is nothing
inside cgi-data there is as below

total 16
drwxr-xr-x 3 root     root     4096 2009-05-26 09:21 .
drwxr-xr-x 5 root     root     4096 2009-05-26 09:20 ..
drwx------ 2 www-data www-data 4096 2009-05-20 11:49 nontmp

The directories "cgi-bin" and "cgi-data" has to be outsite of my
HTML document root directory. cgi-data has to be owned by my
www-data, cgi-bin has to be owned by root, but readable by my
www-data.
webserver is www-data

lex1:popcorn:

---

### Post by Boondoklife on 2009-05-26
Right now your directories are owned by root and should be readable by any user, are you getting an error?

If you look at the security bits you see rwxr-xr-x this means the owner can read/write/execute files the group can read/execute and anyone else can read/execute.

---

### Post by lex1 on 2009-05-26
both directories(cgi-bin and cgi-data) are in the wrong place they have to be  OUTSIDE MY html root directory with those permissions and ownership as in my last post 
like maybe i suggested in /var/www/modified

lex1

---

### Post by Alekz_ on 2009-05-26
IF you only want to change the files' directory, copy the files to the path you wish

```
cp -Rp /source/ /destiny
```

'-p' means that the file permissions won't be changed!

---

### Post by Boondoklife on 2009-05-26
> **Alekz_ said:**
> IF you only want to change the files' directory, copy the files to the path you wish

```
cp -Rp /source/ /destiny
```'-p' means that the file permissions won't be changed!


or more specific```
cp -Rp cgi-bin/ modified
cp -Rp cgi-data/ modified
```

but I would not consider this outside, to me that would be above the /var/www folder ex. /var/cgi-stuff. but that just may be how im reading the words.

---

