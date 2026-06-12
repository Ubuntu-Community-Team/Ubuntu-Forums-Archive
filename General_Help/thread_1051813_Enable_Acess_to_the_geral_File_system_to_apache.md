---
title: "Enable Acess to the geral File system to apache"
date: 2009-01-27
forum: General Help
---

### Post by dinesh707 on 2009-01-27
Hi,

i have installed apache2, php and nagios into a ubuntu system. Now i need to enable all the files and folders to be accessed by a php script which runs on nagios(Which runs on apache-as i know). 

the folder that i wanted to acess is /usr/local/nagios/etc

i need to access all the files and folders inside that folder.  

what can i do??

---

### Post by indytim on 2009-01-27
Here's one way to do it via the terminal mode:

```

$sudo chgrp <your login id> /usr/local/nagios/etc
$sudo chown <your login in> /usr/local/nagios/etc

```

The code above will change the group and folder ownership to your login id.  See :
```

$man chown
$man chgrp

```

for more details as well as additional flags you might want to set.

IndyTim

---

### Post by dinesh707 on 2009-01-27
But its not helping me at all.

does there any settings to set inside apache configuration files??

---

### Post by mcduck on 2009-01-27
one trick you could do is to link that directory into Apache's own document root..

```
sudo ln -s /usr/local/nagios/etc /var/www/etc
```

---

### Post by dinesh707 on 2009-01-27
when i run the php file which tries to acess the file system, apache error.log file shows up somehting like this.

My apache user name is www-data

the log shows:
[notice] caught SIGTERM, shutting down
[notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch configured -- resuming normal operation

??
the php file is inside the folder
/usr/local/nagios/share/nagios_config

the files that should be acesses are inside the folder 
/usr/local/nagios/etc

so is that error comes becouse of the problem in the rights.
I have given permissions to www-data user to create and delete files.

---

