---
title: "apache2"
date: 2006-09-01
forum: Desktop Environments
---

### Post by redmansk8 on 2006-09-01
Hello I have installed Apache2 using sudo apt-get install apache2 it installed. I can open my browser and type [http://localhost](http://localhost) or [http://ipaddress](http://ipaddress) and it will open apache's sample page. which means the server is working. However when I try to publish files to the web it gives me an error. I have tried to publish files using Nvu and using ws ftp on my windows computer over the network. I'm sure its just a setting off but I'm not sure where to look.

---

### Post by halfvolle melk on 2006-09-01
You can make a dir in your home dir called 'public_html'. You can check the content with [http://ipadress/~username/bla.html](http://ipadress/~username/bla.html)

---

### Post by mssever on 2006-09-01
> **redmansk8 said:**
> Hello I have installed Apache2 using sudo apt-get install apache2 it installed. I can open my browser and type [http://localhost](http://localhost) or [http://ipaddress](http://ipaddress) and it will open apache's sample page. which means the server is working. However when I try to publish files to the web it gives me an error. I have tried to publish files using Nvu and using ws ftp on my windows computer over the network. I'm sure its just a setting off but I'm not sure where to look.
What error do you get? You can look at the logs in /var/log/apache2 for more info. Also, where are you copying files to?

> **halfvolle melk said:**
> You can make a dir in your home dir called 'public_html'. You can check the content with [http://ipadress/~username/bla.html]("http://ipadress/%7Eusername/bla.html")
I think that making files available from [http://machinename/foo.html](http://machinename/foo.html) is preferable to [http://machinename/~user/foo.html]("http://machinename/%7Euser/foo.html"). This is simple if you control your server.

---

### Post by ayoli on 2006-09-01
> **redmansk8 said:**
> I have tried to publish files using Nvu and using ws ftp on my windows computer over the network. I'm sure its just a setting off but I'm not sure where to look.
you have installed apache, good, have installed/configured an ftp server ? if not you can't publish pages over ftp from another computer as you tried.
regards.

---

