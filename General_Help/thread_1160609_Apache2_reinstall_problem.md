---
title: "Apache2 reinstall problem"
date: 2009-05-15
forum: General Help
---

### Post by merlot on 2009-05-15
Hey,

I hope this is the right category to ask this question:

I am using Ubuntu 8.04 (gnome)

After installing apache2 (which was working), I added some modules like php, mysql, python, etc. I realized that php wasn't working. I tried to uinstall apache with all its components and reinstall it (including the modules)... nothing changed. So, I uninstalled everything again and manually deleted /etc/apache2 folder completely to make sure that there is no residue from whatever went wrong in previous trials. When I installed apache again, only certain things are installed. httpd.conf file is empty and it didn't even bother putting apache2 script under /etc/init.d, or any link under rcX.d. 

How can I make it to INSTALL like it has never been installed before? I cleaned the cahce of the package manager, downloaded apache again... nothing worked. I still have a corrupted apache2.

---

### Post by cariboo on 2009-05-15
I would try in a terminal:

```
sudo apt-get purge apache2
```

Instead of reinstalling things when they don't work as expected, just search the forums using google, for eaxample:

```
ubuntu php not working
```

is the way I do it, you should find several threads in [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339") dealing with the same problem.

---

### Post by Bark on 2009-05-16
> **merlot said:**
> 
After installing apache2 (which was working), I added some modules like php, mysql, python, etc. I realized that php wasn't working. I tried to uinstall apache with all its components and reinstall it (including the modules)... nothing changed. So, I uninstalled everything again and manually deleted /etc/apache2 folder completely to make sure that there is no residue from whatever went wrong in previous trials. When I installed apache again, only certain things are installed. httpd.conf file is empty and it didn't even bother putting apache2 script under /etc/init.d, or any link under rcX.d. 

Apache 2 doesn't use httpd.conf, it uses a file called "apache2.conf".

---

### Post by mbeach on 2009-05-16
and some other recommended reading covering some other specifics:
/usr/share/doc/apache2.2-common/README.Debian.gz

---

### Post by merlot on 2009-05-16
Neither installation, nor php gives errors. apt-get installs it without any error. But the apache folder is still messed up. apache2.conf is not even created.

Anyway, I installed it through downloading the source and compiling it.

---

### Post by sajid786 on 2009-05-20
Can you please let me know how you done
how you download and compile i m facing same problem
Thanks

---

