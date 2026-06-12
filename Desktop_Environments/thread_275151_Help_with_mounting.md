---
title: "Help with mounting"
date: 2006-10-10
forum: Desktop Environments
---

### Post by Keymaster on 2006-10-10
How do I make it so that my dual boot (XP/Ubuntu 6.06) machine doesn't automatically mount the two ntfs file systems on my computer.  I want them to be able to be mounted manually by root, but not automatically mounted.  I think this is in the fstab file, but I'm not sure what to edit.  The file currently looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
This is for a dual boot public computer, and is very important.  Thanks

---

### Post by mssever on 2006-10-11
Add noauto to the mount options.
```
[FONT=Courier New]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46**[COLOR=Red],noauto[/COLOR]** 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46**[COLOR=Red],noauto[/COLOR]** 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0[/FONT]
```

---

### Post by Keymaster on 2006-10-11
Thanks.  Oh, do you know how to make it so that my website urls aren't case sensitive?  For example ```
http://earc.dyndns.org:83/**cs**14
``` works but ```
http://earc.dyndns.org:83/**CS**14
``` doesn't work.  Thanks

---

### Post by mssever on 2006-10-11
Are those urls pointing to files on your local machine? If so, you can symlink them, assuming that your server (apache?) is configured to follow symlinks. E.g.,
```
ln -s CS14 cs14
```Remember, though, that Linux filenames are case-sensitive and you can't change that. So you'll have to do something like symlinks for every file and every combination of capitalization. Or, do like almost everyone else and use lowercase only. Most URLs are case-sensitive because they're hosted on *nix boxes.

You might be able to use mod_rewrite to produce a more elegant solution if you're using Apache, but I couldn't tell you how off the top of my head. mod_rewrite is fairly advanced.

---

### Post by Keymaster on 2006-10-15
ln -s CS14 cs14 didn't work.  Apache couldn't restart afterwards.  In <Directory></Directory>
it says something about allowing symlinks (autoconfigured by lampp/xampp)  Where does the symlink go?  I tried it in httpd.conf  Was I in the wrong file?

---

### Post by mssever on 2006-10-17
> **Keymaster said:**
> ln -s CS14 cs14 didn't work.  Apache couldn't restart afterwards.  In <Directory></Directory>
it says something about allowing symlinks (autoconfigured by lampp/xampp)  Where does the symlink go?  I tried it in httpd.conf  Was I in the wrong file?

You need to configure Apache to follow symlinks in an appropriate Directory or VirtualHost section in httpd.conf or in your .htaccess file. See the Apache documentation for details: [http://httpd.apache.org/docs/2.2/mod/core.html#options](http://httpd.apache.org/docs/2.2/mod/core.html#options)

Note that whenever Apache refuses to start, an error message explaining the problem will be written to one of the logs in /var/log/apache2  (assuming you're using Apache 2, otherwise, look in the appropriate directory for your version).

Note also that I've never heard of lampp/xampp, so I don't know how it affects what I said.

---

### Post by Keymaster on 2006-10-17
lampp/xampp is a program designed to create an all-in-one apache, proftpd, php, https, perl, phpmyadmin installation for webserver beginners, or n00bs.  It also helps us lazy people as well.  Just google "lampp" to learn all about it.

---

### Post by mssever on 2006-10-18
Setting up a LAMP server can be quite a chore in some OSes, but Ubuntu isn't one of those. Xampp is actually unnecessary in Ubuntu. You can easily install apache, php, mysql, phpmyadmin, etc. from Synaptic--almost as easily as installing Xampp. But the main reason that using Synaptic is superior to Xampp is because you'll automatically get updates, bug fixes, etc. without having to worry about the proper way to upgrade. Everything is handled automatically. Plus, the Ubuntu versions are much more secure out of the box.

Did you get Apache working?

---

### Post by Keymaster on 2006-10-18
I did get apache working properly.  I used ```
CheckSpelling ON
``` with the mod_speling.c module.  That makes everything work the way I want it to... at least until I discover another cool feature I want my site to have

---

### Post by mssever on 2006-10-18
Great! I didn't think of mod_speling.

---

