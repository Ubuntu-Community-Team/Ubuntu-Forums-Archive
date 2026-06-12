---
title: "upload to apache"
date: 2009-05-27
forum: General Help
---

### Post by philcamlin on 2009-05-27
hi i am running ubuntu 9.04 and i have a server with apache 
instead of carrying my usb around from school to home can i upload to my apache server ?
via ftp or something 

please tell me how lol im a noob i just came from windows like 3 weeks ago:popcorn:

---

### Post by ActiveFrost on 2009-05-27
You need to install FTP server : [http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux](http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux)

---

### Post by Cyberpenguin on 2009-05-27
You can also look at implementing WebDAV: [http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622](http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622).  WebDAV can be mounted on a Windows/Linux/OS X machine as a drive and used like any other locally mounted drive.

---

### Post by jonobr on 2009-05-27
You could use secure copy also,

Depending on where you are going from and to,
if your copying from windows to ubuntu

you could use something like winscp to copy files from one to the other,
its pretty intuitive and allows you to drag and drop files between systems.
If its ubuntu to ubuntu

you could use command line 

from the client machine to the server and to copy across the file <file1>
as the user jonobr 
You would use

```
 scp  <file> jonobr@ipaddress:/home/jonobrhome/Desktop 
```

This would copy your file to my desktop

Switch it around to copy from the server  (desktop) to the localmachine 
```
 scp jonobr@ipaddress:/home/jonobrhome/Desktop <file> 
```



[Here]("http://www.hypexr.org/linux_scp_help.php") are more examples

---

### Post by philcamlin on 2009-05-27
ok so after i do that how would i ftp to my apache directory with the coirrect permissions :)

---

### Post by philcamlin on 2009-05-27
ok so after i do that how would i ftp to my apache directory with the coirrect permissions :)

---

### Post by jonobr on 2009-05-27
Hey

If that response was for me,
you could copy the files to the target of your choice , example I gave was /home/jonobr/Desktop

In your case it would be something like /var/www/directory/

SCP and ftp both copy/transport the file 
ftp does it in an insecure clear text way, you can easily see things like usernames and password exchanges etc , whereas scp does it securely.

Once copied to your target directory check permissions with a 
ls -l and see what your premissions and ownership look like

You could always use the place-> connect to server and select ssh and fill in details if your copying from ubuntu to ubuntu and not happy with command line

Cheers

---

### Post by philcamlin on 2009-05-27
kk thanks :)

---

### Post by whitethorn on 2009-05-27
I second what jonobr says.  Install ssh on your ubuntu machine and use winscp (windows) to log in and copy files between folders.  It's better than ftp (encrypted), and no need to use your apache server.

---

