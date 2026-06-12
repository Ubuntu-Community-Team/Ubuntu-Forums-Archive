---
title: "hmmm I can't seem to disable index list apache2"
date: 2009-06-06
forum: General Help
---

### Post by jcup on 2009-06-06
Hello fellow Ubuntu lovers...

I'm stumped, I simply want to disable the listing of the index on all directories in my www folder

1. I just installed Ubuntu 9.04
2. I updated
3. installed apache2
3. installed php5
4. installed mysql 5
5. installed phpmyadmin
6. created .htaccess in /var/www including the line Options -Indexes
7. create folder in www with document.txt 
8. open browser - [http://localhost/folder](http://localhost/folder)
9. IT LISTS THE INDEX!

I read up a bit, and also tried adding 

<Directory /var/www>
 Options -Indexes
 AllowOverride All
 Order allow,deny
 Allow from all
</Directory>

to the httpd.conf file

Still the index is listed

I googled for about two hours without any love

I've done this before, I know my way around ubuntu and apache, I really can't figure out why this isn't working...

Did they change something in the latest version of apache?
Does it have something to do with phpmyadmin?
Can the experts here help me?

Thank you all in advance

jcup

---

### Post by jenkinbr on 2009-06-06
did you restart the Apache2 server.

```
sudo apache2ctl restart
```

then try again.

---

### Post by jcup on 2009-06-06
Yeah, forgot to mention that, I restarted it, even tried rebooting the machine for some reason...


Thanks for the quick reply

---

### Post by jenkinbr on 2009-06-06
> **jcup said:**
> I read up a bit, and also tried adding 

<Directory /var/www>
 Options -Indexes
 AllowOverride All
 Order allow,deny
 Allow from all
</Directory>

to the httpd.conf file



Try this again, but this time, after the directory, make it read /var/www/*, like so:

```
<Directory /var/www/*>
Options -Indexes
AllowOverride All
Order allow,deny
Allow from all
</Directory>
```

I just tried this on my server and I got the expected 403 Forbidden that we are looking for.

---

### Post by jcup on 2009-06-06
Solved!

Now why didn't I think of that... you rock!

Thanks

---

### Post by jenkinbr on 2009-06-06
> **jcup said:**
> Solved!

Now why didn't I think of that... you rock!

Thanks

Human error - we all are guilty

You're welcome - Glad to help!

---

