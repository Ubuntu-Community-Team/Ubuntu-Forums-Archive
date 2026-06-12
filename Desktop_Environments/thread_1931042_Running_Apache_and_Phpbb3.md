---
title: "Running Apache and Phpbb3"
date: 2012-02-24
forum: Desktop Environments
---

### Post by Azubah on 2012-02-24
I had Apache working properly at first I had Mysql installed the only problem was that Phpbb3 had no files in it from Synaptic so I went to the Phpbb site and laoded the files, I had a hard time figuring out how to get into the filesystem with permission to write the phpbb files to the folder. However when I finished with that Apache seemed to no longer work.

I've tried to Reinstall apache and Mysql. But it says the connection timed out like it's getting to much traffic now.

I'm currently on Ubuntu version 10.10 or 10.04 the one right below the upgrade to 11

---

### Post by lisati on 2012-02-24
I'm not sure why you're getting the time out.

When I first had a look at PhpBB I used this guide: [https://help.ubuntu.com/community/PhpBB3](https://help.ubuntu.com/community/PhpBB3)

---

### Post by Azubah on 2012-02-24
That fixed the problem with running it now apache is working and lets me onto it. However it says I do not have permission to access phpbb on the server

ah I'm running Ubuntu 10.10(Maverick)
I got the server to work for phpbb for the most part however there is an overlapping alias so it says it'll likely never match? And it gives a general error. better to show 192.168.1.4/phpbb

If i have it run at the end of the apache2.conf file include /etc/phpbb3/apache.conf it says the above error.

I've got it o so it shows the phpbb folder but it doesn't let me install or run phpbb at all now =/

---

### Post by Azubah on 2012-02-24
Ok scratch all of that I managed to get the server running but now I can't make the proper files read and writable through gksudo nautilus in the /var/www/phpbb folder.

I got it to accept the chmod commands so that is accomplished but now I have the error of

Could not connect to the database, see error message below.
Access denied for user 'admin'@'localhost' (using password: YES)

Should I reinstall mysql and dbconfig-common?

again scratch that I had everything running. I've even forwarded it to the port it wants to use and when I did as the board said to change the permissions to 640 or 644 it made the /phpbb forbidden.

---

