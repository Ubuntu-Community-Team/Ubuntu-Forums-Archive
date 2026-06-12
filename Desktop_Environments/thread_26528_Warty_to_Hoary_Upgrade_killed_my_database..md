---
title: "Warty to Hoary Upgrade killed my database."
date: 2005-04-13
forum: Desktop Environments
---

### Post by GOwin on 2005-04-13
I know, I should've made the backups even if it was only an experimental server but ... :(

Anyway, is this normal during upgrades? I'm a linux newbie and only starting to wean myself off from windows. 

In windows, I would expect the database remain untouched.

(Or is there a way to get back those data?)

---

### Post by p!=f on 2005-04-13
[QUOTE=GOwin]I know, I should've made the backups even if it was only an experimental server but ... :(

Anyway, is this normal during upgrades? I'm a linux newbie and only starting to wean myself off from windows. 

In windows, I would expect the database remain untouched.

(Or is there a way to get back those data?)[/QUOTE]
"My printer does not print. What shall I do?" kind of question. :) Well, I don't have a crystal ball here so let me ask you some questions first... ;)
What database server? 
What was upgraded? 
What's in the logs? 
How did you run upgrade?
What's ```
dpkg -l | grep -v ^ii
``` saying?
How does your /etc/apt/sources.list look like?

---

### Post by GOwin on 2005-04-13
Ooops. Sorry for that ovesight.

I was using postgres that came originally with warty.

here's what I get from the code you posted.

> 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  antiword       0.35-1         Converts MS Word files to text and ps
rc  fam            2.7.0-5ubuntu2 File Alteration Monitor
rc  gnome-cpufreq- 0.1.3-1        CPU Frequency Scaling Monitor applet for GNO
rc  libfam0c102    2.7.0-5ubuntu2 client library to control the FAM daemon
rc  libgtop2-4     2.8.0-0ubuntu1 Libraries for gtop system monitoring library
rc  libnautilus2-2 2.8.1-0ubuntu1 libraries for nautilus components - runtime
rc  libopenh323-1. 1.13.4-3       H.323 aka VoIP library
rc  libpt-1.6.3    1.6.5-3ubuntu1 Portable Windows Library
rc  mergeant       0.12.1-2       GNOME Database admin tool GUI for GNOME2
rc  mgetty         1.1.31-1       Smart Modem getty replacement
rc  pgadmin3       1.0.2-5ubuntu1 Graphical administration tool for PostgreSQL
iF  postgresql     7.4.7-2ubuntu2 object-relational SQL database management sy
rc  smstools       1.14.3-1       SMS Server Tools for GSM modems
rc  trashapplet    0.4-0ubuntu1   Trash applet for GNOME.
rc  xserver-xfree8 4.3.0.dfsg.1-6 the XFree86 X server


Thanks for the response.

---

### Post by shakin on 2005-04-13
What do you mean by "killed"? Can you still access the database using the command line or any local GUI tools? Is it just a PHP app that can't access it (eg phppgadmin)?

If it's just a PHP app that can't access it then in all likelyhood you need to enable the universe repository and install the proper php module... php-postres or something like that. A dist-upgrade wouldn't have found that module in the main repository so you would have lost that functionality.

Neither an upgrade or a dist-upgrade will destroy your database unless PostgreSQL itself has some sort of bug, but I doubt that would have gotten into the official repository.

---

### Post by GOwin on 2005-04-13
Your answer gives me hope that the database is still there somewhere.

I can't access postgres

```
su - postgress
```
results in "su: Authentication failure"

My test installation of egroupware can't use postgres.

in the postgres log, i found this: "FATAL: could not create lock file "/var/run/postgresql/.s.PGSQL.5432.lock": permission denied.

Initially, I found thru google that this could be caused by errors in the permissions. I checked out the folder and it's files and it was owned by root instead of user postgres. 

After changing the permissions, i still get the same error message.

also, when i add new apps via synaptic, i notice this line:
> 
pg_hba.conf contains a field after the authentication specification; the file is corrupt or has already been converted.
dpkg: error processing postgresql (--configure): subprocess post-installation script returned eror exit status 9.


$ dpkg --get-selections postgresql
> postgresql                                      install

 $ dpkg -s postgresql
> --snip--
Conffiles:
 /etc/postgresql/pg_hba.conf 2ec14365922bdbe4add9b83e342bd402
 /etc/postgresql/pg_ident.conf 13315f01db0ad8a8638326b9f035c896
 /etc/logcheck/violations.ignore.d/logcheck-postgresql 56140ea2fefe72cc34b461267f8dc975
 /etc/logcheck/ignore.d.paranoid/postgresql 3baad38bef168f2e265fdbb10ef96039
 /etc/logcheck/ignore.d.server/postgresql 3baad38bef168f2e265fdbb10ef96039
 /etc/logcheck/ignore.d.workstation/postgresql 3baad38bef168f2e265fdbb10ef96039
 /etc/cron.d/postgresql 23a8c41418e73b8e9f63d15b0a5a17a0
 /etc/logrotate.d/postgresql 8822ce30bcea0aad31febb60793fe7bc
 /etc/init.d/postgresql ccd68a90f9ffdf0d9d876a9edd13d701

--snip--

:-?

---

### Post by shakin on 2005-04-13
Try running 'chmod 777 -r /var/run/postgresql' and then see if the lock file can be created. Take note of what the permissions currently are (ls -la) so you can revert if this is insecure.

---

### Post by GOwin on 2005-04-13
[QUOTE=shakin]Try running 'chmod 777 -r /var/run/postgresql' and then see if the lock file can be created. Take note of what the permissions currently are (ls -la) so you can revert if this is insecure.[/QUOTE]

chmod 777 **-R** /var/run/postgresql

what about the lock file? Could you expound on this a bit?

---

### Post by shakin on 2005-04-13
[QUOTE=GOwin]chmod 777 **-R** /var/run/postgresql

what about the lock file? Could you expound on this a bit?[/QUOTE]

Well... I don't know other than the postgres log is complaining about permissions. The file in question is /var/run/postgresql/.s.PGSQL.5432.lock, but that filename looks sort of like it might be generated each time postgres tries to start, so I suggested making the directory and everything under it (that's what -r means) 777 and see if postgres will then start. If not, then I would suggest reinstalling postgres, which shouldn't change your databases.

btw, you should run the chmod command with sudo.

---

### Post by GOwin on 2005-04-13
[QUOTE=shakin]If not, then I would suggest reinstalling postgres, which shouldn't change your databases.

[/QUOTE]

Let me confirm that again. It shouldn't delete my database if I reinstall it? (ie in Synaptic, mark postgres for reinstallation?)

---

### Post by p!=f on 2005-04-14
Looks like your installation of PostgreSQL is broken:
```

iF postgresql 7.4.7-2ubuntu2 object-relational SQL database management sy

```
Note that rc status is just fine. It means you removed a package not purge it so config files were not deleted.
Try to reinstall it:
```

sudo apt-get --reinstall install postgresql

```
If it doesn't help backup your databases
```

sudo apt-get --purge remove postgresql
sudo apt-get install postgresql

```
Hope it helps.

---

### Post by GOwin on 2005-04-14
Thanks for the continous help. Appreciate it much.

I tried re-installing as advised but i get this:

> Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postgresql (7.4.7-2ubuntu2) ...
pg_hba.conf contains a field after the authentication specification;
the file is corrupt or has already been converted.
dpkg: error processing postgresql (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by p!=f on 2005-04-15
Did you also try the second hint given? :)
Backup your database, move pg_hba.conf config file to your backup location or just rename it to .old and purge / install postgresql as mentioned above.

Give us a note if it works.

This paper is worth a read:
[http://www.faqs.org/docs/ppbook/c15679.htm](http://www.faqs.org/docs/ppbook/c15679.htm)

---

### Post by GOwin on 2005-04-17
[QUOTE=p!=f]
[/code]
If it doesn't help backup your databases
```

sudo apt-get --purge remove postgresql
sudo apt-get install postgresql

```
Hope it helps.[/QUOTE]

Sorry for being so dense.

Does this command backup my database?

If not, how do i do it since i don't have access to PG.

---

### Post by p!=f on 2005-04-18
[QUOTE=GOwin]Sorry for being so dense.

Does this command backup my database?

If not, how do i do it since i don't have access to PG.[/QUOTE]
No. That commands will remove / purge / install PostgreSQL. Consult manual pages and documentation how to back up your database.
I thought you install PostgreSQL on your computer...

---

### Post by GOwin on 2005-04-18
Yes. I did have postgres in Warty.

This came up after the upgrade to Hoary.

---

### Post by GOwin on 2005-04-27
I would only to report that Warty didn't actually kill the database.

It was there all along, but a complete installation seems to be being prevented by a configuration file, which I manually removed (not before making a copy).

I followed the advise to purge postgresl before doing a reinstallation. It was working ok after that. (Not really. Not until I modify my firewall configuration, which was blocking access to the database from my groupware application.)

Oh well, at least (I think) I learned some from this experience. Honestly, I don't think I lasted this long with any other Linux distro. :)

(I still got an issue about [XFCE 4.2 and my screen settings (which works ok under gnome)](http://ubuntuforums.org/showthread.php?t=28588), maybe someone can help?)

Thanks.

---

