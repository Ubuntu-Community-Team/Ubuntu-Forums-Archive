---
title: "Mythbuntu hostname change"
date: 2008-12-22
forum: General Help
---

### Post by cbaron0185 on 2008-12-22
Hey everyone, 
I have been looking high and low for 2 lines of SQL code, I want to change the hostname of my mythbuntu server, but I know that if I change it I will lose comm with the backend database. There is a line of SQL code, that will go through the database and change all the old hostnames to the new ones. I want to make server1 and change it to server1.domain.com. If you guys have ideas where I can find that sql code or know it please let me know. 

Thank you

---

### Post by bluefrog on 2008-12-22
use  your-database;
update table set field = new_value where field = condition-value;

---

### Post by cbaron0185 on 2008-12-23
Great,
Thats what I was looking for, I will give it a try a little later. 

Thanks

---

### Post by cbaron0185 on 2008-12-23
> **bluefrog said:**
> use  your-database;
update table set field = new_value where field = condition-value;

I was doing a little more digging and I found this:
When changing the hostname of your system, you must perform the following actions before you start any MythTV programs. If you start a MythTV program before modifying the hostname in the database, the program will create new entries with the new hostname, meaning that the following procedure is likely to fail because of duplicate entries.

It is also critical to ensure you do not change the name of a host to the name of another already-existing host in the database--doing so will cause duplicate entries. Instead, if necessary, run the command below multiple times, using a temporary "placeholder" hostname to ensure the different hosts are not improperly merged.

Note that changing the hostname is performed on an existing database and does not restore a database. Therefore, to change a hostname, ensure that the database exists (restore an old database, as above, if necessary) and execute the following command, replacing "XXXX" and "YYYY" with appropriate values for the old and new hostnames, respectively: 

mythconverg_restore.pl --change_hostname --old_hostname="XXXX" --new_hostname="YYYY"

Is this the best way to do it you think? 

thanks

---

