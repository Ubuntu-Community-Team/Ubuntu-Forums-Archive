---
title: "How to Create a website link."
date: 2006-01-15
forum: General Help
---

### Post by jazee on 2006-01-15
I'm looking for a way to create a link of some sort to a website ftp address. So it would look like another folder but was a link to an ftp server. I need it so that I can get my website editors to work off the server insted of trying to do it localy.

---

### Post by flight_master on 2006-01-15
Hello,

Quick and dirty way:

```

cd Documents/ 
ln -s ftp://link-to-ftp.com MyWebsite

```

If you now go into your Documents folder, you will find a link called MyWebsite. You can use that to interface the FTP server.

Regards,
Christian

---

### Post by jazee on 2006-01-15
Well I tried that and in the termanial I get ""No such file or directory" error. In the GUI I get "The Link is Broken. Do you want to move it to the trash?" Then I have to use the termanial to remove the link. GUI delete wont delete it.

Any other ideas to try.

---

### Post by amohanty on 2006-01-15
Try:
Places->Connect to Server

HTH
AM

---

### Post by jazee on 2006-01-15
That works but now how do I get to that location threw the file tree or terminal. Also how do you remove them out of the places menu.

---

### Post by jazee on 2006-01-16
Any ideas on how to get to the path the mount that it created is at or any other ideas out there to connect to an ftp server as a folder

---

### Post by cwaldbieser on 2006-01-16
[QUOTE=jazee]Any ideas on how to get to the path the mount that it created is at or any other ideas out there to connect to an ftp server as a folder[/QUOTE]
This looks like what you are describing:
[http://lufs.sourceforge.net/]("http://lufs.sourceforge.net/")

---

### Post by quonsar on 2006-01-16
[QUOTE=jazee]Well I tried that and in the termanial I get ""No such file or directory" error. In the GUI I get "The Link is Broken. Do you want to move it to the trash?" Then I have to use the termanial to remove the link. GUI delete wont delete it.

Any other ideas to try.[/QUOTE]

yes, THINK! obviously, you need to HAVE a Documents directory before you can cd or link to it!

---

