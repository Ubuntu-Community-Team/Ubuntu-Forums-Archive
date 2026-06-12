---
title: "Apache [403 Forbidden error] How to fix it ?"
date: 2005-11-15
forum: Desktop Environments
---

### Post by edurm on 2005-11-15
I wish to map URLs to folders outside /var/www/

than I went to [Ubuntuguide.org](http://www.ubuntuguide.org/#mapURLstofoldersoutsidewww) and I did exactly as said. I set the /bb directory 

I created a directory in home/bbuser/www  *bbuser is the user that created the directory 


It suppose to works like this; when I hit [http://localhost/bb](http://localhost/bb) it should take me to /home/bbuser/www I put an index.html there but it keep saying I have no permision, why?

I already tryied chmod 666 and chmod 777 :???: 

*I made some searchs in database but nothing :( 


any ideas ?



thks 'n advanced

---

### Post by suRoot on 2005-11-15
Please post what you entered in the alias file.  Also, please post the output of 

```
ls -l /home/bbuser/www
```

---

### Post by wrtrdood on 2005-11-15
If your links are correct, it's probably because the webserver doesn't own the files (and directories) or cannot get access to them.

---

### Post by edurm on 2005-11-15
[QUOTE=suRoot]Please post what you entered in the alias file.  Also, please post the output of 

```
ls -l /home/bbuser/www
```[/QUOTE]




Alias
> 
Alias /bb /home/bbuser/ww1/

<Directory /home/bbuser/ww1/>
   Options Indexes FollowSymLinks
   AllowOverride All
   Order allow,deny
   Allow from all
</Directory>




ls -l

> 
root@ubuntu:/home/bbuser/ww1# ls -l
total 12
-rw-r--r--  1 bbuser root 9459 2005-11-15 17:09 index.htm
-rw-------  1 bbuser root    0 2005-11-15 16:36 index.html~
root@ubuntu:/home/bbuser/ww1#



---

### Post by edurm on 2005-11-15
[QUOTE=wrtrdood]If your links are correct, it's probably because the webserver doesn't own the files (and directories) or cannot get access to them.[/QUOTE]


first I put and index.html and then I rename to index.htm, if I can't fix it I'll try chmod 777 /var/www (hope it works) 


Thks for helping me out

---

