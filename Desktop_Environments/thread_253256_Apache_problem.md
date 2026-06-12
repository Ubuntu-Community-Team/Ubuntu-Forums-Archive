---
title: "Apache problem"
date: 2006-09-08
forum: Desktop Environments
---

### Post by horatiub on 2006-09-08
I can't figure out why my website don't work when I type the address without the www in front of the site name.

Basically, if I type [www.name.com](www.name.com) it works fine, but not without the www. I configured the sites-available in apache such as the server name is [www.name.com](www.name.com) and the Server Alias is name.com and still nothing.

Any ideas?

Thank you

---

### Post by horatiub on 2006-09-08
anybody?

---

### Post by tturrisi on 2006-09-08
did you restart apache after making the changes?

---

### Post by horatiub on 2006-09-08
yes I did.

---

### Post by khaledaboualfa on 2006-09-08
unrelated question here (kind of) but how do you stop and start apache? I've installed lampp and it works fine, however there seems to be another apache working in parallel, and for some reason I can't seem to stop it.

I've tried :** /usr/share/apache2ctl stop**

and that gives me the following:  [B]apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[/B]

I've tried :  /etc/init.d/apache2 stop

and that seems to work, but for some reason it starts up again when I log in again. Is there a way to stop it and only have the lampp apache come up?

---

### Post by hc2995 on 2006-09-08
do you have a domain name? if so you have to edit the confing file so that apache knows that NAME.com is its domain

---

### Post by horatiub on 2006-09-08
> **hc2995 said:**
> do you have a domain name? if so you have to edit the confing file so that apache knows that NAME.com is its domain

Yes, I do have a domain name, but I'm not sure which config file you're refering to.

---

### Post by horatiub on 2006-09-09
bump

---

### Post by horatiub on 2006-09-09
still nobody?

---

### Post by openmind2k5 on 2006-09-18
Try make a virtual host for name.com in the httpd.conf (at the bottom if i remember well) . 

I hope it helps
openmind


[URL="http://www.tornado-templates.com"]
flash templates[/URL]

[banner design]("http://www.bannerslaunge.com")

[plantillas flash]("http://plantillas.tornado-templates.com")

---

### Post by trac on 2006-10-09
add ServerName localhost at the end of the conf-file, that should do it.

---

