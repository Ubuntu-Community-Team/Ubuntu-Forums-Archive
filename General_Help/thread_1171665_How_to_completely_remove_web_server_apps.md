---
title: "How to completely remove web server apps?"
date: 2009-05-27
forum: General Help
---

### Post by litlfrog on 2009-05-27
I wanted to try out a couple of content management systems: SilverStripe and WordPress. Long story short, I'm unhappy with SilverStripe and want to try WordPress. I deleted the SilverStripe directory from my Home folder, but WordPress takes me to a localhost screen that I recognize from SilverStripe, so I must not have deleted something. I'd like to completely get rid of both, but I don't know how to go about that.

---

### Post by litlfrog on 2009-05-30
Bumped for great justice!

---

### Post by ActiveFrost on 2009-05-30
Can you rephrase your question ( I don't understand what you want ) ?
By the first, what's your web server home directory ( not users home directory ), which version of Apache/PHP/MySQL you are running, how you installed these /apps/ ( though, I wouldn't call Wordpress an application ), etc.
Give us a bit more info about what and where you've installed & what/from where you've deleted ;)

---

### Post by litlfrog on 2009-05-31
I'm afraid I don't know what my web server home directory is--I remember following instructions to edit a configuration file months ago, but I don't know where it was. I'm using apache2 installed through apt-get at the command line. I didn't install MySQL separately--it came with either apache2 or php. The version of PHP was whatever is in Synaptic Package Manger for Jaunty Jackalope.

What I want is to try the WordPress content management system, but while it installed correctly (no errors, at least) I can't get to a login screen; I keep getting "host not found." I don't have any important work saved on this system, so I thought the easiest way to make sure things are configured correctly would be to delete old programs and configuration files and start again.

---

### Post by ActiveFrost on 2009-05-31
In that case, /var/www/ - if you haven't changed it, all your files should be there ( otherwise you'll see "not found" error ).

```
cd /var/www/
ls -l
```

Can you show us the output ?

---

### Post by litlfrog on 2009-05-31
Here's the output of that command.
> -rw-r--r-- 1 globalnet globalnet  107 2009-05-31 14:12 index.html
lrwxrwxrwx 1 root      root        20 2009-05-27 13:11 localhost -> /usr/share/wordpress
-rw-rw-r-- 1 globalnet globalnet 9187 2009-05-01 16:51 orderform_printable.php~
-rw-r--r-- 1 globalnet globalnet 1624 2009-05-01 16:51 shipping_table.php~


---

### Post by litlfrog on 2009-05-31
Thanks anyway, but I think I'm going to go about this differently. I've tried removing and reinstalling apache, php, and mysql, but I a) can't log in to mysql through the command line even after creating a password and b) can't even get the default localhost page to load in my web browser with apache2 started. I hate the thought of reinstalling over something so dumb, but I need to step away from this. It's very frustrating to not just be able to uninstall and reinstall the program and have it work the way it did on the first install. For right now, I'm going to try to get apache to at least show the page properly in my browser.

---

### Post by ActiveFrost on 2009-05-31
No need to reinstall something .. /var/www/ is your localhost ! Remove all files from that dir and all your web applications will disappear ( the same if you want to install - do it in /var/www/ ).
Anyway, good luck ;)

---

