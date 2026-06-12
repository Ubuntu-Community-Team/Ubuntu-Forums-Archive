---
title: "Web Server"
date: 2009-05-06
forum: General Help
---

### Post by arthursc on 2009-05-06
Hi,

Former windows user...

I would like to know if there is a localhost webserver that can be installed to 9.04 desktop?

Could someone point me to a reliable source with simple instructions.

Thanks
Colin

---

### Post by prem1er on 2009-05-06
[http://www.lighttpd.net/](http://www.lighttpd.net/)

It is in the repos also.

```
apt-get install lighttpd
```

---

### Post by dacorr on 2009-05-06
Apache2, is should be in the repos,

sudo apt-get install apache

from terminal should do it

then /var/www/ is the webserver root

Dac

---

### Post by albinootje on 2009-05-06
> **arthursc said:**
>  I would like to know if there is a localhost webserver that can be installed to 9.04 desktop?


Open a terminal, and run :
```

sudo apt-get install apache2

```
After that try [http://localhost/](http://localhost/) in your web browser.
Files go under /var/www/
The configuration files are here : /etc/apache2/
Logfiles here : /var/log/apache2/

---

### Post by Wiebelhaus on 2009-05-06
> **albinootje said:**
> Open a terminal, and run :
```

sudo apt-get install apache2

```
After that try [http://localhost/](http://localhost/) in your web browser.
Files go under /var/www/
The configuration files are here : /etc/apache2/
Logfiles here : /var/log/apache2/

Just to reiterate what this user posted , sound advice.

---

### Post by colau on 2009-05-06
> **albinootje said:**
> Open a terminal, and run :
```

sudo apt-get install apache2

```
After that try [http://localhost/](http://localhost/) in your web browser.
Files go under /var/www/
The configuration files are here : /etc/apache2/
Logfiles here : /var/log/apache2/
Is there any command to stop and start the server manually from terminal?

---

### Post by prem1er on 2009-05-06
> **colau said:**
> Is there any command to stop and start the server manually from terminal?

```
/etc/init.d/apache2 stop
```

---

### Post by arthursc on 2009-05-06
Thanks all...I knew it should be there but when I searched the add/remove applications I could not see it.

---

### Post by mcduck on 2009-05-06
..and in case you want the whole LAMP stack instead of just Apache:

```
sudo tasksel install lamp-server
```
(or, in Synaptic, go to Edit/Mark Packages by Task & enable the "LAMP Server"-option.

This will install & configure Apache, MySQL and PHP. I suggest installing the phpmyadmin package as well to get a nice browser-based interface for MySQL management.

---

### Post by colau on 2009-05-06
> **prem1er said:**
> ```
/etc/init.d/apache2 stop
```
Thanks prem1er.

---

### Post by albinootje on 2009-05-06
> **arthursc said:**
> Thanks all...I knew it should be there but when I searched the add/remove applications I could not see it.

I've been showing some brand new Linux users about Add/Remove (because it looks easy), but even when "all available applications" was chosen for the repositories of it, it still didn't find all applications, while Synaptic Package Manager does find it all.
So I try to tell them stick to Synaptic PM, while I stick to "apt-cache search" and apt-get+dpkg myself.

---

### Post by mcduck on 2009-05-06
> **albinootje said:**
> I've been showing some brand new Linux users about Add/Remove (because it looks easy), but even when "all available applications" was chosen for the repositories of it, it still didn't find all applications, while Synaptic Package Manager does find it all.
So I try to tell them stick to Synaptic PM, while I stick to "apt-cache search" and apt-get+dpkg myself.

The Add/Remove-thing (gnome-app-install) isn't really meant to be a full-blown package management tool but instead just easier way to install & remove a selection of the most commonly used applications. There's no way it could be that if it listed all the packages available in repositories and gave all the tools and options Synaptic has.

It really is a great tool for what it's made for. Installing software couldn't possibly be easier and simpler. You just shouldn't think of it as a package manager as it really isn't one.

---

