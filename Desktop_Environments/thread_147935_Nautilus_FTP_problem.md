---
title: "Nautilus FTP problem"
date: 2006-03-21
forum: Desktop Environments
---

### Post by vibestriton on 2006-03-21
I cannot access a certain login FTP site via Nautilus but can access that same site with any other FTP program (including gFTP and lftp).  Every other login FTP site I have tried to access via Nautilus has worked.
The problem FTP site runs Windows FTP Server (Version 4.0) and is a remote machine to which I don't have direct access.  Any thoughts on what could be causing this?

(By the way, this problem exists in both Breezy and Dapper, I have no firewalls running, and I have a direct connection to the internet.)

---

### Post by tedius on 2006-03-21
I'm having a similar problem ([Nautilus and ftp]("http://www.ubuntuforums.org/showthread.php?t=146886")).

I have narrowed it down to accounts that I have a username containing an "@".

Is this the same as your problem?

---

### Post by vibestriton on 2006-03-21
No. The account username and password uses alpha-numeric characters only.

---

