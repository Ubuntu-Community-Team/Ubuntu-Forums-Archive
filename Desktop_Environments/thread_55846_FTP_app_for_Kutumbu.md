---
title: "FTP app for Kutumbu"
date: 2005-08-10
forum: Desktop Environments
---

### Post by Owdy on 2005-08-10
Dont like gFTP. Is there any good ftp software for G? Like Filezilla in windows.

---

### Post by roland on 2005-08-10
[QUOTE=Owdy]Dont like gFTP. Is there any good ftp software for G? Like Filezilla in windows.[/QUOTE]

Ncftp is a very good ftp client, though it only has a commandline interface. Nevertheless, after a small study, it becomes very handy. The package ncftp is available in universe, so you have to check your /etc/sources.list file.

Maybe you can take a look [here](http://linuxreviews.org/software/ftp-clients/), I'm also going to try some.

---

### Post by Sahtor on 2005-08-10
KFTPGrabber:
[http://kftpgrabber.sourceforge.net/](http://kftpgrabber.sourceforge.net/)

You can find that program in DinTon repository
[http://dinton.no-ip.org/](http://dinton.no-ip.org/)

---

### Post by jeremy on 2005-08-10
There is also KBear in the repos, but I prefer gFTP.

---

### Post by Owdy on 2005-08-10
[QUOTE=Sahtor]KFTPGrabber:
[http://kftpgrabber.sourceforge.net/](http://kftpgrabber.sourceforge.net/)

You can find that program in DinTon repository
[http://dinton.no-ip.org/](http://dinton.no-ip.org/)[/QUOTE]
That looks good. Thank you!

---

### Post by shakin on 2005-08-10
You could always just use the Linux version of Filezilla. Filezilla 3 will support Windows and Linux and you can get nightly builds right now. I used one a few months ago and it was quite good.

[http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php)

---

### Post by rosslaird on 2005-08-10
What about plain 'ol konqueror?

It works great with the kioslaves for ftp and shh.
I use a split screen (source/destination) and never have any trouble.

---

### Post by Owdy on 2005-08-10
[QUOTE=shakin]You could always just use the Linux version of Filezilla. Filezilla 3 will support Windows and Linux and you can get nightly builds right now. I used one a few months ago and it was quite good.

[http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php)[/QUOTE]
THANKKKSS!!! :D

> Originally Posted by Sahtor
KFTPGrabber:
[http://kftpgrabber.sourceforge.net/](http://kftpgrabber.sourceforge.net/)

You can find that program in DinTon repository
[http://dinton.no-ip.org/](http://dinton.no-ip.org/) Hmm, that crashes a lot. 

[QUOTE=rosslaird]What about plain 'ol konqueror?

It works great with the kioslaves for ftp and shh.
I use a split screen (source/destination) and never have any trouble.[/QUOTE]Only thing, it wont remember passwords. And does it know when use binary and ascii automaticly?

---

### Post by rosslaird on 2005-08-10
[QUOTE=Owdy]Only thing, it wont remember passwords.[/QUOTE]

You may have something specific in mind, but k remembers my password as long as the application is open (maybe you want it to remember passwords between different sessions, but I don't think even gftp does that.) Besides, I usually use shh and I have set myself up for passwordless logins, so it's not an issue for me.

> And does it know when use binary and ascii automaticly?

I don't have any trouble with this either. K seems to get it right.

---

### Post by Owdy on 2005-08-10
[QUOTE=rosslaird]You may have something specific in mind, but k remembers my password as long as the application is open (maybe you want it to remember passwords between different sessions, but I don't think even gftp does that.) Besides, I usually use shh and I have set myself up for passwordless logins, so it's not an issue for me.



I don't have any trouble with this either. K seems to get it right.[/QUOTE]
 Ok, thank you. How do i enable SSH?

---

### Post by rosslaird on 2005-08-10
There are various guides on how to do this. Here's one from a quick google for "ssh passwordless login"

[http://members.optusnet.com.au/~rickfrm/help/passwordless_ssh.html](http://members.optusnet.com.au/~rickfrm/help/passwordless_ssh.html)

Or look at my backup tutorial for rsync and ssh:

[http://ubuntuforums.org/showthread.php?t=15082](http://ubuntuforums.org/showthread.php?t=15082)

ssh is not that hard to setup, and it's far more secure then ftp.

Ross

---

