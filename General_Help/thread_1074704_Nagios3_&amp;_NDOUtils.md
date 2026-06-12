---
title: "Nagios3 &amp; NDOUtils"
date: 2009-02-19
forum: General Help
---

### Post by mihamil on 2009-02-19
I have install nagios3 and ndoutils with the commands:
sudo apt-get install nagios3
sudo apt-get install ndoutils-nagios3-mysql

I added the broker module line to nagios.cfg

changed the line ENABLE_NDOUTILS=0 to 1 in the ndoutils init script.

When I "sudo invoke-rc.d ndoutils start"  I get the following error.

Starting ndoutils: invoke-rc.d: initscript ndoutils, action "start" failed.

Both installed successfully and the database was created but no data appears to be going into it.  I have restarted nagios and the entire server but cannot figure out how to get everything to feed into the database.

Did I miss a step?

---

### Post by jonathanmotes on 2009-05-30
I'm having this same problem. Anyone know the fix?

---

### Post by Orio91 on 2009-06-26
A had the same problem today.
You need to tell nagios to load the ndoutils module.
In the nagios.cfg configuration file add this to the event broker module section:
```
broker_module=/usr/lib/ndoutils/ndomod-mysql-3x.o config_file=/etc/nagios3/ndomod.cfg
```Restart nagios3 and check the nagios log, if everthing is right, you should see something like that:
```
ndomod: NDOMOD 1.4b7 (10-31-2007) Copyright (c) 2005-2007 Ethan Galstad (nagios@nagios.org)
ndomod: Successfully connected to data sink.  0 queued items to flush.
Event broker module '/usr/lib/ndoutils/ndomod-mysql-3x.o' initialized successfully.

```

---

### Post by AjitJor on 2009-07-14
My opinion is totally different from the ones expressed here, regarding the use of Synatptic or Apt for Nagios and its addons installation. 

The paths in which the Nagios installation places the different files creates a situation in which (post-install) adding the various Nagios addons and plugins (with their never ending config files and most importantly: various paths) becomes a configuration nightmare. Some addons just take for granted that your installation is at /usr/local/nagios/. Apt places stuff at /etc/nagios3. The default Apache cgi path of the vanilla Nagios is at [http://localhost/nagios](http://localhost/nagios) whereas with apt it should be directed to /localhost/nagios3 ... and this is just to get the cgi going.

These are my suggestions regarding installing Nagios and NDOutils:

[http://www.nagios-portal.org/wbb/index.php?page=Thread&postID=105957&h#post105957](http://www.nagios-portal.org/wbb/index.php?page=Thread&postID=105957&h#post105957)

Good luck - your going to need it ...
Amit

---

### Post by Black Trench Coat on 2011-08-10
I'm trying to use the Ubunto 10.04 NDOutils packages

ndoutils-common
ndoutils-doc
ndoutils-nagios3-mysql

Documentation says run db/installdb to create tables in the database.
I'm googling and checking other sources and they agree on this step.
I find no db directory and no db/installdb script in these packages.
Is there some other package? I'm getting ready to try downloading and
building NDOutils myself.

---

### Post by Black Trench Coat on 2011-08-10
Hmm.  Somehow I missed this the first time around, but the
install does create tables in the MySQL database, under the
'ndoutils' schema.

There are some helpful hints in 

/usr/share/doc/ndoutils-nagios3-mysql/README.Debian
/usr/share/doc/ndoutils-nagios3-mysql/README.gz

The Ubuntu packagers have actually done a lot of the work
for you... all I really needed to do was edit 


/etc/nagios3/nagios.cfg
/etc/nagios3/ndo2db.cfg

and

/etc/default/ndoutils.

---

