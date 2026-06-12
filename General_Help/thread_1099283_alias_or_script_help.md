---
title: "alias or script help"
date: 2009-03-18
forum: General Help
---

### Post by infallible on 2009-03-18
I want a command to enable an apache virtual host - ie
"deploy website"
results in 
cp /etc/apache2/sites-available/website.conf /etc/apache2/sites-enabled/website.conf
#AND
/etc/init.d/apache2 restart

I tried adding it as an alias (without apache restart, just the copy) but using "$1" as well as "%1"; based on someone elses thing that does something else that i didn't understand. But, I digress...

i get a "no such file or directory" error when attempting to use the above described alias. can anyone help me to accomplish this?

---

### Post by adult swim on 2009-03-18
does this work?
add to your .bashrc
```
alias deploy='sudo cp /etc/apache2/sites-available/website.conf /etc/apache2/sites-enabled/website.conf'
``` and then run it with deploy.  i couldnt figure out how to add a space to the alias, neither \ or ' ' worked.

---

### Post by infallible on 2009-03-18
That works. If I have a file called website.conf. I could have an alias for every virtual host, but I want to have the * of *.conf be variable, so that "deploy 'variable'" results in a copy of 'variable'.conf being made.

---

### Post by lloyd_b on 2009-03-18
Unfortunately, you cannot use "$" parameters with aliases.  But you *can* do so with a shell function:```
function deploy(){ sudo cp /etc/apache2/sites-available/$1.conf /etc/apache2/sites-enabled/$1.conf; sudo /etc/init.d/apache2 restart; 
```and then just type "deploy website".  This can be added to "~/.bashrc", just like an alias.  Note: I'm assuming that you aren't running the command as root to begin with (hence the sudo's).

Lloyd B.

---

### Post by fieroboom on 2009-03-18
The purpose of having sites-available and sites-enabled is so that you can symlink from available to enabled, making it easy and space-saving to enable/disable virtual hosts.
My advice would be to create a simple script in /usr/local/bin. Perl is my weapon of choice, so here's how I'd do it:
```
gksudo gedit /usr/local/bin/deploy-website
```
And in that file, here's the code I'd put:
```

#!/usr/bin/perl

use strict;

if (!$ARGV[0]) { print "Usage: deploy-website <site_name>\n"; exit; }

else{ system("ln -s /etc/apache2/sites-available/$ARGV[0] /etc/apache2/sites-enabled/ && /etc/init.d/apache2 restart"); }
```
Then you need to make it executable:
```
sudo chmod 755 /usr/local/bin/website-deploy
```
And here's what it does... without any cmd line arguments:
```
vps-pallen:~# sudo deploy-website
Usage: deploy-website <site_name>
```

I created a 'site' called 'test':
```
vps-pallen:~# touch /etc/apache2/sites-available/test
```
and then tried it out:
```
vps-pallen:~# sudo deploy-website test
Forcing reload of web server (apache2)... waiting .

vps-pallen:~# ls -al /etc/apache2/sites-enabled/
total 8
drwxr-xr-x 2 root root 4096 2009-03-18 01:09 .
drwxr-xr-x 7 root root 4096 2009-03-04 22:24 ..
lrwxrwxrwx 1 root root   42 2009-01-15 12:01 alabamafieros -> /etc/apache2/sites-available/alabamafieros
lrwxrwxrwx 1 root root   36 2008-11-06 08:10 default -> /etc/apache2/sites-available/default
lrwxrwxrwx 1 root root   37 2008-11-06 08:10 default~ -> /etc/apache2/sites-available/default~
lrwxrwxrwx 1 root root   41 2008-11-06 08:10 fierofactory -> /etc/apache2/sites-available/fierofactory
lrwxrwxrwx 1 root root   40 2008-11-06 08:10 grandesigns -> /etc/apache2/sites-available/grandesigns
lrwxrwxrwx 1 root root   39 2008-11-06 08:10 jazlyncami -> /etc/apache2/sites-available/jazlyncami
lrwxrwxrwx 1 root root   43 2008-11-06 08:10 lynnmariemason -> /etc/apache2/sites-available/lynnmariemason
lrwxrwxrwx 1 root root   42 2008-11-06 08:10 pacificfieros -> /etc/apache2/sites-available/pacificfieros
lrwxrwxrwx 1 root root   41 2008-11-06 08:10 resumesender -> /etc/apache2/sites-available/resumesender
lrwxrwxrwx 1 root root   44 2008-11-06 08:10 southeastfieros -> /etc/apache2/sites-available/southeastfieros
lrwxrwxrwx 1 root root   45 2008-11-06 08:10 terryyoungrealty -> /etc/apache2/sites-available/terryyoungrealty
lrwxrwxrwx 1 root root   33 2009-03-18 01:09 test -> /etc/apache2/sites-available/test
```
Also, it's not the best practice to put sudo within a script... If you run the parent process (the script) as sudo, then any child processes it spawns, like a system call, will assume super user permissions as well.
:D
-Paul

---

### Post by infallible on 2009-03-18
Both of these solutions should do what I'm looking for. The linked node script is optimal, fieroboom; will I need to set a FollowSymLinks flag for apache anywhere, or is the usage of that flag limited to content directories? I also noticed that your script and example didn't have .conf extensions - do you have a workaround in place to enable this?

---

### Post by fieroboom on 2009-03-18
> **infallible said:**
> Both of these solutions should do what I'm looking for. The linked node script is optimal, fieroboom; will I need to set a FollowSymLinks flag for apache anywhere, or is the usage of that flag limited to content directories? I also noticed that your script and example didn't have .conf extensions - do you have a workaround in place to enable this?

FollowSymlinks is for the web content directories, not for Apache's own configuration.

In Apache2, the only .conf files that need the .conf extension are /etc/apache2/apache2.conf & /etc/apache2/ports.conf

That perl script will *deploy* whatever file you give it for the command-line argument, so if I had created a 'test.conf' in the sites-available folder, I would have deployed it with:
```
sudo website-deploy test.conf
```
Let me know if I need to explain it better.
:D
-Paul

---

### Post by infallible on 2009-03-18
Thanks for the help.

---

