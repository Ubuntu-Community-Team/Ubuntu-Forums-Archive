---
title: "Can't find php binary"
date: 2006-01-05
forum: Desktop Environments
---

### Post by terriblynice on 2006-01-05
As the topic title ... I can't find my php binary.

I don't understand why I can't find the binary.  I've gone as far as doing a 
 [CENTER]find / | grep -i php [/CENTER]
and looking for it that way.

---

### Post by rubinstein on 2006-01-05
Why do you need a php binary?
I have a php5 module installed for apache (sudo apt-get install apache2 libapache2-mod-php5) and also can't find a binary with "which php".

Can you install a stand-alone php-binary?

You have to move your web pages to /var/www and open it in a webbrowser ([http://127.0.0.1/](http://127.0.0.1/)) then php will be interpreted.

---

### Post by terriblynice on 2006-01-05
[QUOTE=rubinstein]Why do you need a php binary?[/QUOTE]

I have a programme that requires PHP.

> Can you install a stand-alone php-binary?

I have a php binary already installed.  I can't find it, hence my question.

---

### Post by rubinstein on 2006-01-05
[QUOTE=terriblynice]
I have a php binary already installed.  I can't find it, hence my question.[/QUOTE]
Where did you get the php binary? How did you install it?
If it was a .deb package you can start the synaptic package manager and view the installed files of the package when you select "properties" and "installed files".

---

