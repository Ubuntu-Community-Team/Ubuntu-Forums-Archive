---
title: "Is my website hacked?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by anil_robo on 2006-08-31
I'm running a website from a very old computer - Ubuntu Dapper, Apache and php4. I built virtual hosts in my home directory. I created the website folders in my home dir using mkdir command, and did not edit the permissions etc.

Google analytics tells me that I get few hits from ubuntuforums (obviously, I post the link here, so I should get traffic from here), but also from a site [www.animeupload.com](www.animeupload.com). But I can't find any link to my site on animeupload.com

I am suspecting that someone has hacked my webserver and put his files in there - I can't see any though.

Can someone tell me how to tell if I'm hacked, and how do I set the permissions correctly?

Thanks

---

### Post by mssever on 2006-08-31
If someone put files on your server, then you should be able to see them. The traffic you saw from that other site is probably the result of the Referer [*sic*] header. There could have been a link to yoursite there at one time, or someone's browser could have incorrectly reported the referrer. That header isn't terribly reliable.

As far as parmissions go, the server shouldn't have write access to your files unless you have a reason to give it that access. Of course, the files must be readable by the server process. You should also disable any other servers that you're running that you don't need. For example, do you need FTP? SSH? sendmail?

---

### Post by closet geek on 2006-08-31
Look into tripwire, chkrootkit and rkhunter, they'll let you know if something bad has happened, well the last two will the first is useless to you now but useful to install once you're sure everything is ok.

Most hacks come via PHP and that normally means (as PHP runs as an Apache module in most cases) that files placed on a server via a PHP exploit have the user nobody. Run this command in your public_html:

ls -lAh | grep nobody

If you see any strange looking files then you could be in trouble.

Check /tmp for suspicious files then mount your /tmp directory as no-exec, use this if you want to do it for you:

cd /dev/; dd if=/dev/zero of=tmpMnt bs=1024 count=250000; mke2fs -F /dev/tmpMnt; cp -Rp /tmp /tmp_backup; mount -o loop,noexec,nosuid,rw /dev/tmpMnt /tmp; chmod 0777 /tmp; cp -Rp /tmp_backup/* /tmp/; umount -l /var/tmp/; rm -rf /var/tmp/; ln -s /tmp/ /var/; rm -rf /tmp_backup
echo "/dev/tmpMnt             /tmp                    ext2    loop,noexec,nosuid,rw 0 0" >> /etc/fstab

Hope that helps.

cg

---

### Post by anil_robo on 2006-08-31
> **mssever said:**
> As far as parmissions go, the server shouldn't have write access to your files unless you have a reason to give it that access. Of course, the files must be readable by the server process. You should also disable any other servers that you're running that you don't need. For example, do you need FTP? SSH? sendmail?

I use secure FTP (SFTP) to put files on my website (designed using dreamweaver on a mac 5 miles away from the server). I tried setting read only permissions to everyone except myself (and root of course) to all files and directories in the website, but goofed up (I'm new to CLI) and the site was down. So I reset the permissions to original, and they're now like this:

drwxr-xr-x  2 akumar akumar  1024 2006-08-26 20:45 css
drwxr-xr-x  2 akumar akumar  1024 2006-08-26 20:45 downloads
drwxr-xr-x  2 akumar akumar  1024 2006-08-26 20:45 flash
drwxr-xr-x  2 akumar akumar  4096 2006-08-26 21:02 graphics
drwxr-xr-x 12 akumar akumar  1024 2006-08-26 21:04 html
drwxr-xr-x  6 akumar akumar  1024 2006-08-26 21:04 images
-rw-r--r--  1 akumar akumar 19696 2006-08-30 21:48 index.html
drwxr-xr-x  9 akumar akumar  1024 2006-08-31 18:24 isearch2
-rw-r--r--  1 akumar akumar  1521 2006-08-29 01:10 resources.txt
drwxr-xr-x  2 akumar akumar  1024 2006-08-29 01:10 templates

Is this an okay configuration?

---

### Post by mssever on 2006-08-31
> **closet geek said:**
> Most hacks come via PHP and that normally means (as PHP runs as an Apache module in most cases) that files placed on a server via a PHP exploit have the user nobody. Run this command in your public_html:

ls -lAh | grep nobody
Actually Apache by defult runs as www-data in Ubuntu. Running ```
ps -ef | grep apache
``` will tell you what user apace is running as. Then modify the ls code above to use the proper user instead of nobody.

> **anil_robo said:**
> I use secure FTP (SFTP) to put files on my website (designed using dreamweaver on a mac 5 miles away from the server). I tried setting read only permissions to everyone except myself (and root of course) to all files and directories in the website, but goofed up (I'm new to CLI) and the site was down. So I reset the permissions to original, and they're now like this:

drwxr-xr-x  2 akumar akumar  1024 2006-08-26 20:45 css
drwxr-xr-x  2 akumar akumar  1024 2006-08-26 20:45 downloads
drwxr-xr-x  2 akumar akumar  1024 2006-08-26 20:45 flash
drwxr-xr-x  2 akumar akumar  4096 2006-08-26 21:02 graphics
drwxr-xr-x 12 akumar akumar  1024 2006-08-26 21:04 html
drwxr-xr-x  6 akumar akumar  1024 2006-08-26 21:04 images
-rw-r--r--  1 akumar akumar 19696 2006-08-30 21:48 index.html
drwxr-xr-x  9 akumar akumar  1024 2006-08-31 18:24 isearch2
-rw-r--r--  1 akumar akumar  1521 2006-08-29 01:10 resources.txt
drwxr-xr-x  2 akumar akumar  1024 2006-08-29 01:10 templates

Is this an okay configuration?
The file permissions look fine. Remember, Apache doesn't run as root, so they have to be readable by everyone.

---

### Post by anil_robo on 2006-08-31
> **mssever said:**
> Actually Apache by defult runs as www-data in Ubuntu.
But I'm running apache as root! ```
sudo apache2
``` 
> Running ```
ps -ef | grep apache
``` will tell you what user apace is running as. Then modify the ls code above to use the proper user instead of nobody. This is the output:
```
akumar@ubuntu:~$ ps -ef | grep apache
root     10260     1  0 17:59 ?        00:00:02 apache2
www-data 10430 10260  0 19:04 ?        00:00:00 apache2
www-data 10431 10260  0 19:04 ?        00:00:00 apache2
www-data 10432 10260  0 19:04 ?        00:00:00 apache2
www-data 10433 10260  0 19:04 ?        00:00:01 apache2
www-data 10434 10260  0 19:04 ?        00:00:00 apache2
www-data 10435 10260  0 19:04 ?        00:00:00 apache2
www-data 10436 10260  0 19:04 ?        00:00:00 apache2
www-data 10437 10260  0 19:04 ?        00:00:00 apache2
akumar   10522 10412  0 19:18 pts/0    00:00:00 grep apache
akumar@ubuntu:~$ 
``` 

> The file permissions look fine. Remember, Apache doesn't run as root, so they have to be readable by everyone. 
I remember I had to run apache as root because I wanted my virtualhosts dirs in my home dir, and apache wasn't quite willing to accept that... unless I ran it as root. If I run apache as normal user, it gives me this error:
```
akumar@ubuntu:~$ apache2
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
``` 

 Is this bad? I feel it is! :!:

---

### Post by mssever on 2006-08-31
Actually, you're running Apache as www-data. Notice that there's only one root-owned proocess in your ps output. The worker processes are all running as www-data.

Here's how Apache works: In order to bind to ports lower than 1024, you have to be root. Most websites run on port 80. So, you start Apache as root. Apache binds to port 80 and then switches to running as www-data (or whatever user it's configured to run as).

So, you're OK from that perspective. By the way, the canonical way to control Apache is ```
sudo apache2ctl start
sudo apache2ctl stop
sudo apache2ctl graceful #reload configuration without taking server down
```

---

### Post by anil_robo on 2006-08-31
> **mssever said:**
> Here's how Apache works: In order to bind to ports lower than 1024, you have to be root. Most websites run on port 80. So, you start Apache as root. Apache binds to port 80 and then switches to running as www-data (or whatever user it's configured to run as).
Thanks for the assistance and reassurance. From the horse's mouth: [click here.]("http://httpd.apache.org/docs/2.0/invoking.html")

---

### Post by tturrisi on 2006-08-31
Install Webalizer which will parse the server logs and generate html files and you can then view the server stats using [http://ipaddress/stats/](http://ipaddress/stats/) and you can then see the referrers and everything else.  afaik google analytics won't read the apache log files.

---

### Post by mssever on 2006-09-01
> **tturrisi said:**
> Install Webalizer which will parse the server logs and generate html files and you can then view the server stats using [http://ipaddress/stats/](http://ipaddress/stats/) and you can then see the referrers and everything else.  afaik google analytics won't read the apache log files.

Google Analytics can't read the log files, but provided that the user has Javascript enabled (most do), it can actually get a lot more info than webalizer can. IMO Google Analytics is superior to Webalizer--although you might benefit at times from using both.

---

### Post by anil_robo on 2006-09-14
> **mssever said:**
> IMO Google Analytics is superior to Webalizer--although you might benefit at times from using both.

Tried, and found so! Thanks for the hint :)

---

### Post by pod25 on 2006-09-14
This has nothing to do with your thread, however - - 

I visited your site and it's full of pop-up scripts, I frigging hate pop-ups, and people who use such scripts on there web sites are total dicks.

But thats just my opinion.

---

### Post by anil_robo on 2006-09-14
> **pod25 said:**
> I visited your site and it's full of pop-up scripts, I frigging hate pop-ups, and people who use such scripts on there web sites are total dicks.

I fully agree with you, but where are the popups in my site? I hope you looked at the site in my signature.

---

