---
title: "Using FTP with simple backup confic tool"
date: 2009-05-08
forum: General Help
---

### Post by kurtfagerburg on 2009-05-08
I want to use the simple backup config tool to store backups on an ftp site so that my backups are not stored locally.  Can anyone recommend an ftp site that can be used like this?

---

### Post by kurtfagerburg on 2009-05-10
Looks like ADrive.com may be what I'm looking for.  I'll test it out and see how it works.  They have a free 14-day trial.

---

### Post by kurtfagerburg on 2009-05-11
Got an FTP account with adrive.com.  I can connect using FileZilla but I can't seem to get the tool to talk to the ftp server.  My connection string on the destination tab of the Simple Backup Config Tool looks like this:

[ftp://username:password@ftp.adrive.com:21](ftp://username:password@ftp.adrive.com:21)

I've verified username and password using FileZilla but when I click the Test button on the Destination tab I receive the message that the selected destination is not writable with current permissions.  I'm pretty sure I don't have the connection string constructed correctly.  

Can anybody help?

---

### Post by hms_matteo on 2009-05-11
Hello,

Have you attempted to write a file to the destination server using FileZilla to see if your user has the proper permissions to write to ftp.adrive.com? I don't have the "simple backup config tool" in front of me right now to judge what the connection string should be, but from the error you are receiving it sounds like it can connect but not put files to the server.

---

Matt Pellegrino :: Support Engineer :: mpellegrino @ hostmysite.com :: [www.HostMySite.com]("http://www.HostMySite.com?utm_source=bb")

---

### Post by kurtfagerburg on 2009-05-11
I tried using FileZilla and successfully connected to the site.  I think I found what the problem is, though.

My username for the site has an '@' in it because it is my email address.  The connection string specified in the backup config tool 

[ftp://kurtfagerburg@domain.com:](ftp://kurtfagerburg@domain.com:) [email]password@ftp.adrive.com[/email]

I think that the multiple '@' signs are confusing the tool.

---

### Post by shane2peru on 2009-05-13
Check out this: [http://ubuntuforums.org/showthread.php?t=1054386](http://ubuntuforums.org/showthread.php?t=1054386)  Post #15 I give a simple solution to automate this process.  Put your locale backups in one directory then set it up to run like show there.

Shane

---

