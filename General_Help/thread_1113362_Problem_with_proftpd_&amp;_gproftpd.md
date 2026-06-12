---
title: "Problem with proftpd &amp; gproftpd"
date: 2009-04-01
forum: General Help
---

### Post by NoPantsJim on 2009-04-01
I've tried to setup an FTP server for my own home use using the following thread:

[http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp](http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp)

I used this command:

sudo apt-get install proftpd gproftpd

but once I attempted to start the GUI by going to:

Applications - System Tools - GADMIN-PROFTPD

and got the following message:

"Could not launch menu item. Failed to execute child process "su-to-root"(No such file or directory)"

Help?

---

### Post by jonobr on 2009-04-01
NoPantsJim, wow , thats a scary handle

I Did a google using your error and there is a thread [Here]("http://http://ubuntuforums.org/archive/index.php/t-970110.html") which may help

---

### Post by Return Privacy on 2010-10-15
Hi all,
I also tried to install proftpd and gproftpd. It will NOT install gproftpd, it says it is not found. All that installs is proftpd-basic. So, there is absolutely NO GUI to configure this FTP server.
Something was removed, because you can not get gproftpd to install from anywhere.

---

### Post by Refalm on 2010-10-15
GProFTPd is pretty horrible. You can use the ProFTPd module for Webmin though.

---

### Post by Return Privacy on 2010-10-15
Hi All,
I just spent all night searching and trying to install an FTP server on Ubuntu 10.04. What a bunch of BS! Proftpd wouldn't work, and there is NO GUI for it available (gproftpd). So, I tried PureFTPd. Same problems, you have to install it from command line, and then it won't work anyway. I also found a reference to "PureAdmin", which is supposed to be the graphical front end to make PureFTPd work. It would have been nice if someone had explained just how to install PureAdmin! A few more hours, an finally found something that mentions you have to use an application to install the "package". I finally got PureAdmin installed. That should have been the end of it, but wrong. I followed the How-to on here for installing and setting up PureFTPd with commands, and then using PureAdmin to add users and such. Well, after ALL night of trying, it still won't work. It seems that PureFTPd won't authenticate ANY user that trys to login and upload a file. I followed the How-To on Ubuntu's forums for setting this up, word for word, letter for letter, (including their sample name and group name) it is in the community documentation for PureFTPd. Well, I've got some news for whoever wrote that up, they are wrong. I can't believe that something that should be very simple to do, is almost impossible to do on Ubuntu? 
-Yeah, I know I sound angry, that's because staying up all night working on something that should be easy to do, _won't work at all_. You would think that a simple FTP server would be a basic thing for Ubuntu 10.04?

---

