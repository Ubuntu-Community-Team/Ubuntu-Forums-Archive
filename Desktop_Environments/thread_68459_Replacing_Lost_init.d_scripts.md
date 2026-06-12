---
title: "Replacing Lost init.d scripts"
date: 2005-09-23
forum: Desktop Environments
---

### Post by tweak on 2005-09-23
I inadvertantly deleted the apache2 and mysql /etc/init.d/ scripts (ok... I did it on purpose and now I need them again, hence the red face emoticon). Is there an easy way to get them back? I don't feel comfortable with trying to create my own given the apparent complexity of existing ones.

Any help would be much appreciated.

---

### Post by garlito on 2005-09-23
I would try to uninstall apache an then reinstall again:

apt-get remove apache2
( That keeps your system configuration files )
apt-get install apache2

That's the fastest way if you've got the packages in the cache.

You can also download the package ( apache2-common, I think ), extract files and put the script in its place by hand

You can extract doing:

dpkg --extract apache2-common_2.0.53-5ubuntu5.3_i386.deb .
That extracts in the current directory

---

### Post by Dooglus on 2005-09-23
[QUOTE=garlito]I would try to uninstall apache an then reinstall again:

apt-get remove apache2
( That keeps your system configuration files )
apt-get install apache2

That's the fastest way if you've got the packages in the cache.

You can also download the package ( apache2-common, I think ), extract files and put the script in its place by hand

You can extract doing:

dpkg --extract apache2-common_2.0.53-5ubuntu5.3_i386.deb .
That extracts in the current directory[/QUOTE]
 I'd suggest doing:

  sudo apt-get --reinstall install apache2-common mysql-server

(or whatever the package names are).

Incidentally, you can find out which package contains a given file by installing the 'apt-file' package, then running "sudo apt-file update" to download the list of package contents, and then:

    apt-file search /etc/init.d/mysql
    apt-file search /etc/init.d/apach

---

### Post by mlomker on 2005-09-23
[QUOTE=tweak]I inadvertantly deleted the apache2 and mysql /etc/init.d/ scripts (ok... I did it on purpose and now I need them again, hence the red face emoticon).[/quote]

You could always use the 'reinstall' option in Synaptic to restore all of the original files.

Not sure why you deleted the init.d scripts, but there are other ways to manage the rc?.d files if that's why you did it.

---

### Post by bsussman on 2005-09-23
Re-install is too extreme just to retrieve one file - especially one that it is unlikely you modified, and is not modified by install (i think)

From google search:

 > A deb package is a ar (shell archive) file.  "ar -x" will unarchive it.
 You can do this in a temporary directory and select files to your
 desire. 
 
 Thus you can retrieve it from the package in your archive directory
**  IN A NEW EMPTY DIRECTORY - I MEAN IT**
 ```

> ar -x /var/cache/apt/archives/apache2-common_2.0.53-5ubuntu5.3_i386.deb            
> tar zvft data.tar.gz | grep apache2.conf
```
 
 Got me close - untarring the tar.gz and copying the file is all that's left
 ```

> tar zvfx data.tar.gz
> cd etc
> cd init.d
``` 

and there it is...

---

### Post by tweak on 2005-09-23
[QUOTE=bsussman]
 ```

> ar -x /var/cache/apt/archives/apache2-common_2.0.53-5ubuntu5.3_i386.deb            
> tar zvfx data.tar.gz
> cd etc
> cd init.d
> cp apache2 /etc/init.d/
```[/QUOTE]

That worked a treat, however mysql doesn't want to start using BUM. It reports a "Failed command execution". Is there a nice way to diagnose what might be causing the start failure?

---

### Post by bsussman on 2005-09-23
nice?? I doubt it.

It looks like /var/log/daemon.log is where mysql logs - this might be a start.

What happens when you start it from the commandline?

I do not use BUM so I dunno.

---

### Post by Dooglus on 2005-09-23
[QUOTE=bsussman]nice?? I doubt it.

It looks like /var/log/daemon.log is where mysql logs - this might be a start.

What about starting it from the commandline?

I do not use BUM so I dunno.[/QUOTE]
 Did you remember to make the init script executable?

"sudo chmod 755 /etc/init.d/mysql-server"

(or whatever the script is called)

---

### Post by amanda on 2007-07-05
And next time you want to disable some init.d scripts, try being a little more gentle:

```
sudo chmod -x /etc/init.d/apache2
```

will prevent it from loading.

---

