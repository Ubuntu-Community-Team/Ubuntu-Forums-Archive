---
title: "Unable to see ALL FreeBSD Samba Shares from Nautilus"
date: 2006-04-10
forum: Desktop Environments
---

### Post by 3x3cvt0r on 2006-04-10
Hi!  I have a Samba Server running on FreeBSD 6.0 and Samba 3

I can all ten shares i deployed when Im using any Windows XP.  And all of the access works using any username and password i have created for the server.

however, I can get it to work with my Ubuntu Desktop.  Using Nautilies, I can only see 3 out of 10 shares i have created.  Can anyone help me troubleshoot??

Thanks.

---

### Post by 3x3cvt0r on 2006-04-11
Please help, I really need this to get this to work...:confused: ](*,)

---

### Post by 3x3cvt0r on 2006-04-16
:( no help?

---

### Post by gotthardt on 2006-04-19
I just posted this:
[http://ubuntuforums.org/showthread.php?t=162481&highlight=samba](http://ubuntuforums.org/showthread.php?t=162481&highlight=samba)

We might not have the same real problem - my server is running out of file handles because Nautilus is opening so many. Check with:
sysctl kern.openfiles to see how many files are open - I normally have around 160 open, but it can be in the thousands very quickly by browsing with Nautilus. I raised the number of files to 40000 from 7000 ot avoid crashes. But you will still have a problem if you keep browsing.

This must be fixed! I added some comments to a bug report:
[https://launchpad.net/malone/bugs/34116](https://launchpad.net/malone/bugs/34116)

I hope this gets fixed! I have stopped using Dapper as a development platform since it cannot mount project shares.
Good Luck
Steve

---

### Post by 3x3cvt0r on 2006-04-19
[QUOTE=gotthardt]I just posted this:
[http://ubuntuforums.org/showthread.php?t=162481&highlight=samba](http://ubuntuforums.org/showthread.php?t=162481&highlight=samba)

We might not have the same real problem - my server is running out of file handles because Nautilus is opening so many. Check with:
sysctl kern.openfiles to see how many files are open - I normally have around 160 open, but it can be in the thousands very quickly by browsing with Nautilus. I raised the number of files to 40000 from 7000 ot avoid crashes. But you will still have a problem if you keep browsing.

This must be fixed! I added some comments to a bug report:
[https://launchpad.net/malone/bugs/34116](https://launchpad.net/malone/bugs/34116)

I hope this gets fixed! I have stopped using Dapper as a development platform since it cannot mount project shares.
Good Luck
Steve[/QUOTE]

Thank you for your input. i do see that there are similiraties in our issue.  However in my issue i cannt see the shares to start with. ill try remaking the smb.conf file of the server and see if it resolves the issue.

BTW, I really think this is a show stopper for dapper.  Hope this gets fixed soon!

Thanks again.

---

