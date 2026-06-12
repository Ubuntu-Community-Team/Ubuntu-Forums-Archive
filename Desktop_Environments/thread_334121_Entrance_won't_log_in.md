---
title: "Entrance won't log in"
date: 2007-01-08
forum: Desktop Environments
---

### Post by MrObvious on 2007-01-08
Hello. I've been trying to use the Entrance that comes with E17 as my default dm. However it seems it doesn't like PAM at all. I'd like to be able to get it to log in successfully but all I get is the little lock icon flashing. Here is the syslog:

Jan  8 11:36:14 localhost entrance: Debug: ipc_title = /var/lib/entrance/entrance_ipc_0
Jan  8 11:36:14 localhost entrance: entrance_ipc_init: connect to daemon failed.
Jan  8 11:36:16 localhost entrance: PAM: Authentication service cannot retrieve authentication info..
Jan  8 11:36:18 localhost entrance: entrance_ipc_shutdown: Success

What I've tried:

Copying the .desktop file to /usr/share/xsessions (whatever it is)
Copying several /etc/pam.d/ files ot the entrance file.
Dinking around with various support avenues.

I hope someone has had experience with Edgy + Entrance.

Thanks
Paul

---

### Post by russellc on 2007-01-13
I'm having the same problem. My Entrance won't log me in...

EDIT: I found a problem, but solving the problem didn't let me log in either. I have given up for now, but I will pose my hopeful but failed solution.

Maybe I sound stupid for not doing this when building Entrance originally, but PAM support was not being built (so I found). I found this while in the console after Entrance loaded and some attempts of logging in were made. Went to the source directory and ran the configure script. For some reason, it was complaining that evas wasn't installed because evas-config did not exist in PREFIX/bin. So, I had to export the path in which evas-config existed by running **export PATH=$PATH:/opt/e17/bin:/opt/e17/sbin**. After doing that, the configure script completed, but PAM support was a No. So I figured the PAM developmental libraries weren't installed, so I went ahead and apt-get installed libpam-dev. To my hopefulness, the configure script then ran properly and PAM support was a Yes :D. So I did the standard make and make install and it all installed properly. I restarted Entrance, but unfortunately it still refused to work properly.. So for now, I have given up and am back to GDM. Hopefully a solution will be found for this :)

---

### Post by Sp4rKy on 2007-01-14
Hi guys.

I don't know the way you use to install E17, but let me say you there is Ubuntu repo for E17.
Entrance isn't into now, but it will be included the next week.

So, to use those repo, you can take a [E17 blog]("http://e17blog.tuxfamily.org/home.php/").

I'm happy to help you on irc (#elbuntu at freenode) 8)

---

