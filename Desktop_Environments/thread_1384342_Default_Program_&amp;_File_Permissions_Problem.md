---
title: "Default Program &amp; File Permissions Problem"
date: 2010-01-18
forum: Desktop Environments
---

### Post by buster2209 on 2010-01-18
After my wi-fi connection went screwy on Hardy, I updated to Jaunty.

Everything is going fine with the new distro except two little problems.... I can't set the default program and file permissions.

In order to set a default program, you right click the file you want to open, go to 'Open With' and select 'Open with Other Application' and select a program. Voila, that is now the default program to open that type of file.

I have done this numerous times over the past few days but the default program I pick wont save.

I also have a problem setting file permissions.  

I made a little script to control my computers processor freq if the comp gets too hot, but superuser privileges are required to do this via Terminal.  I have changed the file permission (sudo chown dan -R /sys/devices/system/cpu/) but when I restart, the file permission is back to being root and not the user!

Any help?

---

### Post by buster2209 on 2010-01-20
bump!

---

### Post by mcduck on 2010-01-21
Actually the default program is not set by right-click->Open With. That only selects the program to use that time (allowing you to override the default). To set the default you need to right-click->Properties->Open. 

What comes to the permission issue, trying to change the permissions of system files isn't the way to go. You need to change your own permissions instead. In this case by adding the command you want to be able to run without sudo password into /etc/sudoers file to allow your user to run it without a password.

---

### Post by buster2209 on 2010-01-21
> **mcduck said:**
> Actually the default program is not set by right-click->Open With. That only selects the program to use that time (allowing you to override the default). To set the default you need to right-click->Properties->Open.

Thanks, all sorted now!

> **mcduck said:**
> What comes to the permission issue, trying to change the permissions of system files isn't the way to go. You need to change your own permissions instead. In this case by adding the command you want to be able to run without sudo password into /etc/sudoers file to allow your user to run it without a password.

How can I do this?  I can't figure out how to save a modified sudoers file using visudo.

I want to execute a python script located in my documents with root privileges without being asked for my password.  How and where do I add this?

---

### Post by buster2209 on 2010-01-22
bump!

---

### Post by buster2209 on 2010-01-23
bump!

---

### Post by mcduck on 2010-01-24
This HowTo should prety much cover editing of the sudoers file: [http://ubuntuforums.org/showthread.php?t=1132821]("http://ubuntuforums.org/showthread.php?t=1132821")

---

### Post by buster2209 on 2010-01-24
> **mcduck said:**
> This HowTo should prety much cover editing of the sudoers file: [http://ubuntuforums.org/showthread.php?t=1132821]("http://ubuntuforums.org/showthread.php?t=1132821")

Thanks!

---

