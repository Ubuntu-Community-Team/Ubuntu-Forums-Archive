---
title: "operating an FTP server"
date: 2006-07-25
forum: Desktop Environments
---

### Post by justicerulesok on 2006-07-25
my boss wants ubuntu to be used as an ftp server.  Neither of us know much about ftp servers & I've had three days playing with ubuntu which is three more than him.

We have other servers for email, file handling, printing & network logons.

[COLOR="Red"]the spec i've been given by the bossman is that he wants people to use a scanner connected to a pc downstairs to scan files into a folder on this pc & then go back to there own PC's login & be able to access the folder/files & manipulate them.[/COLOR]

The reason he wants to store the files on this rather than the file server is that the files server is nt4 with 4gb hdd & he cant afford server 2003 for this machine so its ubuntu.

I have fireFTP installed as an extention for firefox.  I don't know if this is suffciant.  I have googled various forums to no avail & downloaded varius ftp progs which I either cant get the service to run or its all in terminal which I'm not any good at yet.

[COLOR="Lime"]Please does anyone have a how to or other suggestions?[/COLOR]

Thank you all your help - sorry it was a long post

Justice.

---

### Post by it.henrik on 2006-07-25
If you want something nice and GUI .. you can have a look at gproftpd.

Why dont just make it a samba share? Make the scanner scan into a folder wich is shared with samba... easy peasy!

---

### Post by justicerulesok on 2006-07-25
Questions

What is samba?
How do i set up a pc to scan into samba?

I do like GUI's as a starting point but I know nothing about ftp's.  As a newbie to this kind of thing I do need a bit of handholding I@m afraid :-/

Thank you for answering.

Justice.

---

### Post by it.henrik on 2006-07-25
> **justicerulesok said:**
> Questions

What is samba?


Google is your friend...
[http://us4.samba.org/samba/](http://us4.samba.org/samba/)

> **justicerulesok said:**
> 
How do i set up a pc to scan into samba?


just save whatever you just scanned in a folder thats being shared by samba.

> **justicerulesok said:**
> 
I do like GUI's as a starting point but I know nothing about ftp's.  As a newbie to this kind of thing I do need a bit of handholding I@m afraid :-/

Thank you for answering.

Justice.

Sorry .. I just hold hand with my GF :) 
The forums here have TONS of info about samba, just do a quick search .. there are lots of howtos and you will find more information in the ubuntuguide.

---

### Post by Thund3rstruck on 2006-07-27
As far as the FTP server goes, I've always loved [Proftpd]("http://www.proftpd.org/"). It's simple to setup and is extremely reliable. 

Follow this [Simple ProFTPd Guide]("http://ubuntuguide.org/wiki/Dapper#FTP_Server") and you'll be serving up files in a matter of minutes.

---

