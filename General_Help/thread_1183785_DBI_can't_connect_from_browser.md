---
title: "DBI can't connect from browser"
date: 2009-06-10
forum: General Help
---

### Post by hthumbo on 2009-06-10
Hi everbody,

I use ubuntu server 9.04 with last perl, mysql server 5.1 and apache 2. I use on my perl script DBI to connect to the mysql database. So when i run any perl script without DBI I can see the result from web browser and when apply #./perlscript.pl or #perl perlscript.pl.

And my problem is that, in my perl script when I use DBI from terminal (#./perlscript.pl or #perl perlscript.pl.) I can see the results from my query and from webbrowser I can't.

The result from error on web browser is:
[COLOR="Red"]
Software error:

DBI connect('::3306','',...) failed: Access denied for user 'www-data'@'localhost' (using password: NO) at /var/www/cgi-bin/test.pl line 28

For help, please send mail to the webmaster (myemail@domain.com), giving this error message and the time and date of the error. [/COLOR]


Thanks,

---

### Post by hthumbo on 2009-06-11
Please anybody can help me?

---

### Post by hthumbo on 2009-06-12
Please help me.

---

### Post by hthumbo on 2009-06-16
Please anybody can help me?

---

### Post by theDaveTheRave on 2009-11-26
hthumbo.

you need to give us more information, try looking at the error logs for the apache server.

From the menu use

Systeme -> Admin -> System Log.

then use the file menu to open the required log file.

Your setup is most likely different from mine, so to find the apace log file try the following

```

locate error.log | grep apache

```

Open it and have a look, these logs are your friend when it comes to debugging your cgi scripts. 


For a quick extra bit of help however...

where you have the [/code]DBI->connect(DBI:serverType..... )[/code] put a copy into the forum post...

It sounds like you have a syntax error in your code, looking at your error message.


David

---

