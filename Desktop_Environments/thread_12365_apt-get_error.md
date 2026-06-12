---
title: "apt-get error"
date: 2005-01-24
forum: Desktop Environments
---

### Post by negatron on 2005-01-24
I'm trying to install webmin, because I think it is easier to configure Samba and other stuff with that. But, I'm having a problem. When I tried to install webmin with 'apt-get install webmin' it said that it's installed. So, next thing was to install webmin-samba. And that's where things started to go wrong. This is what I got:

root@kiipeilyteline:/etc # apt-get install webmin-samba
Reading Package Lists... Done
Building Dependency Tree... Done
webmin-inetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up webmin-inetd (1.150-2) ...
/etc/webmin/webmin.acl: No such file or directory
dpkg: error processing webmin-inetd (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 webmin-inetd
E: Sub-process /usr/bin/dpkg returned an error code (1)

I even tried to install webmin-samba, webmin and webmin-inetd with -f option, still the same error. I can't even remove webmin because of the webmin-inetd.  :cry: 

I'm still learning to use Linux, so I hope you can give simple advices. ;)

edit. Tried to use Synaptic Package Manager, and got rid of webmin. But there's still webmin-inetd that won't go. This is what Synaptic says:

(Reading database ... 82492 files and directories currently installed.)
Removing webmin-inetd ...
/var/lib/dpkg/info/webmin-inetd.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-inetd (--remove):
 subprocess pre-removal script returned error exit status 1
/var/lib/dpkg/info/webmin-inetd.postinst: line 4: /usr/sbin/update-webmin: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 webmin-inetd

---

### Post by mendicant on 2005-01-24
You can probably try to reinstall webmin.  The easiest way to do so might be to download the package, then use dpkg -i /var/cache/apt/archives/webmin....deb.  Then try to install webmin-inetd again, and remove it afterwards.  update-webmin is in package webmin, so that'll always fail until you install webmin, or fake it.

There are other drastic measures you can try, like dpkg --force-remove-rinstreq, but I wouldn't recommend it yet.

---

### Post by negatron on 2005-01-25
Thanks for help. Tried to reinstall webmin and webmin-inetd. Also tried to reconfigure the webmin-inetd, and then it told me that it couldn't find files /etc/webmin/webmin.acl and /etc/webmin/update.conf. I made empty files with those names and then succesfully removed both webmin and webmin-inetd.
And during this process I learned some new stuff about Linux, again. So thanks for that too  =D>

---

### Post by mendicant on 2005-01-25
Nothing like fooling the config scripts by faking the files.

It's not something I would recommend most of the time, though, as you can't be too sure what the config scripts do unless you download the source package and search through it.

---

### Post by BoBoB on 2005-02-11
I have installed Webmin/samba successfully on several of my machines by using this method:

1. apt-get install webmin webmin-core
2. Update Webmin to the last version (1.180) from inside Webmin itself
3. apt-get install samba 
4. Configure Samba in Webmin

---

