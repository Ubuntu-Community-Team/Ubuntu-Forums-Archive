---
title: "Access to my computer from a remoted machine"
date: 2006-02-23
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-02-23
Hey, I have some files on my computer I would like to let a friend of mine access. They're to big to simply mail them over.

What's the best way to do that?

G

---

### Post by suRoot on 2006-02-23
The safest & easiest thing is to use a service like yousendit...  supports files up to 1GB...

[http://www.yousendit.com/](http://www.yousendit.com/)

---

### Post by GabrielWolff on 2006-02-23
[QUOTE=suRoot]The safest & easiest thing is to use a service like yousendit...  supports files up to 1GB...

[http://www.yousendit.com/](http://www.yousendit.com/)[/QUOTE]

And if I want someone really let have access to my computer, or access my computer myself, but while being at a remoted machine?

---

### Post by suRoot on 2006-02-23
Setup the ssh daemon.  I think there's a how-to in the customization forum / wiki.  You can get console access or use sftp to transfer files.

---

### Post by GabrielWolff on 2006-02-23
[QUOTE=suRoot]Setup the ssh daemon.  I think there's a how-to in the  / wiki.  You can get console access or use sftp to transfer files.[/QUOTE]

>Could you translate that into english? ;)  Like: should I look for "customization forum" at wikipedia?

G

---

### Post by yota on 2006-02-23
He meant the ubuntu's wiki, go to:

[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

---

### Post by SuperBOB on 2006-02-23
Purely for file sharing? then just use an FTP server like VSFTPD

[http://vsftpd.beasts.org/](http://vsftpd.beasts.org/)

---

### Post by Garyu on 2006-02-23
[http://www.ubuntuforums.org/showthread.php?t=91887&highlight=vsftpd+howto](http://www.ubuntuforums.org/showthread.php?t=91887&highlight=vsftpd+howto)
I used this howto to get vsftpd up and running. It sure is easy, and makes you able to access from windows machines as well, and over the internet. Not very secure though.

I tried getting ssh to work before, but I haven't found a howto until now. That tip for using nautilus to browse ssh shares was GREAT. :) (Ctrl-L and then "ssh://<username>@<hostname>"). Thank you very much for the link, it makes my life a whole lot easier. :cool:

---

