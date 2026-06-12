---
title: "xampp on ubuntu 9.10 - Why can't I edit files!?"
date: 2010-03-08
forum: Desktop Environments
---

### Post by longdog on 2010-03-08
Hi all, XAMPP is up and running but when I go to edit files - for instance, the splash.php in File System/opt/lampp/htdocs - It's a 'Read Only'.. AND if I create a simple 'Hello World' php file with gedit I can't save it anywhere in my File System, it says - "No Permission".  

Are there some administration controls I need to unlock or something?  I'm stuck, and it's so early in the process!! ahhh

Thank You

LD

---

### Post by spiderbatdad on 2010-03-08
Ubuntu uses sudo for administrative privileges. So the command ```
sudo -i

``` will begin an administrative session for you. While: ```
sudo some_command
``` will execute a single command with root privileges.

If you are using graphical apps, gedit for example, gksudo, or gksu should be used:
```
gksu gedit /path/to/some/file
```

Permissions can also be changed on files outside of /home/* with the use of sudo chmod. One simple way is assigning numbers to represent permissions, where read=4, write=2, execute=1...for owner,group, and other, in that order.
```
sudo chmod 600 /some/file
``` gives the owner (root in the case of most system files) read, write, while giving no access to anyone else. You will need to familiarize yourself with these and a number of other commands to successfully set up your server. Beware of haphazardly changing the default permissions of system files...this can break your system. But regarding your server files, your safe...if the server isn't working however, it is often due to incorrect file permissions.

[http://www.reallylinux.com/docs/basic.shtml](http://www.reallylinux.com/docs/basic.shtml)

---

