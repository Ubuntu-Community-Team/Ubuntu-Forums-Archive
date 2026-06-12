---
title: "Where is the gdm.conf in Ubuntu 9.10?"
date: 2010-03-21
forum: Desktop Environments
---

### Post by markoid8 on 2010-03-21
I have been working on building a VNC server setup where a user can connect, and is shown the GDM greeter and they can log in and out just like a local user. I have gotten the VNC part to work fine, but when I connect, I get the blank grey X screen.

My reasoning for this is because the guides I have looked at ask me to edit the file /etc/gdm/gdm.conf. This file does not exist in my filesystem. I have even done searches for the file, and it does not appear in any other directory. I have tried to create the file but the changes are not applied.

Has the file been removed, replaced, or changed names?
I really need to be able to make the changes that this file allows to be made.

I have been using Ubuntu for 3 years and I rarely need to pose questions to the forums, but this one has me completely stumped.

My system runs Ubuntu server 9.10, a fairly fresh install. [less than 2 weeks old]

Any help would be much appreciated. Thanks in advance.

---

### Post by diesch on 2010-03-22
Use */etc/gdm/custom.conf*

---

### Post by Moozillaaa on 2010-05-27
My 9.10 doesn't have this file.

Help?

---

### Post by Moozillaaa on 2010-05-27
Found it; not what we're looking for...

---

### Post by PhDLinux on 2010-05-28
In Ubuntu 10.04, users who want to override gdm settings have to create a new file named /etc/gdm/custom.conf in the "keyfile" format. Meanwhile, the system default keys and values are in the human-readable file /etc/gdm/gdm.schemas. If you stare long enough at the XML-style stanzas in there, you can figure out the keys and values it sets. The official documentation at
  [http://library.gnome.org/admin/gdm/stable/configuration.html.en](http://library.gnome.org/admin/gdm/stable/configuration.html.en)
makes a couple of useful points:
  1. The file gdm.schemas is machine-generated, and will be overwritten automatically during upgrades. So editing it is unwise, as the changes may get obliterated without warning.
  2. gdm has been changing a lot lately, and some of the options that were formerly available have gone away.
The cited link provides a detailed list of supported keys and values.

Hopefully these notes apply also to Ubuntu 9.10.

---

### Post by hok00age on 2010-05-28
> **markoid8 said:**
> I have been working on building a VNC server setup where a user can connect, and is shown the GDM greeter and they can log in and out just like a local user. I have gotten the VNC part to work fine, but when I connect, I get the blank grey X screen.

My reasoning for this is because the guides I have looked at ask me to edit the file /etc/gdm/gdm.conf. This file does not exist in my filesystem. I have even done searches for the file, and it does not appear in any other directory. I have tried to create the file but the changes are not applied.

Has the file been removed, replaced, or changed names?
I really need to be able to make the changes that this file allows to be made.

I have been using Ubuntu for 3 years and I rarely need to pose questions to the forums, but this one has me completely stumped.

My system runs Ubuntu server 9.10, a fairly fresh install. [less than 2 weeks old]

Any help would be much appreciated. Thanks in advance.

Read this tutorial, it cover GDM customization too:
[http://dl.dropbox.com/u/6786897/ubuntu_customization.tar.gz]("http://dl.dropbox.com/u/6786897/ubuntu_customization.tar.gz")

---

### Post by athenaa on 2010-07-26
hi PhDLinux,

I have the exact same problem, :(
were you able to solve your problem?

---

### Post by bohemier on 2010-08-03
> **markoid8 said:**
> I have been working on building a VNC server setup where a user can connect, and is shown the GDM greeter and they can log in and out just like a local user. I have gotten the VNC part to work fine, but when I connect, I get the blank grey X screen.

My reasoning for this is because the guides I have looked at ask me to edit the file /etc/gdm/gdm.conf. This file does not exist in my filesystem. I have even done searches for the file, and it does not appear in any other directory. I have tried to create the file but the changes are not applied.

Has the file been removed, replaced, or changed names?
I really need to be able to make the changes that this file allows to be made.

I have been using Ubuntu for 3 years and I rarely need to pose questions to the forums, but this one has me completely stumped.

My system runs Ubuntu server 9.10, a fairly fresh install. [less than 2 weeks old]

Any help would be much appreciated. Thanks in advance.

Hello everyone! markoid8, were you successful on setting up vnc to show gdm ? I've been searching to accomplish the same on my ubuntu server 10.04 box...

So far, I've been able to open the gnome session in the vnc session by putting gnome-session & ONLY in ~/.vnc/xstartup :

```
#!/bin/sh
gnome-session &

```

It all works well, I get my gnome session, but it skips login... I'd rather login normally into the session with gdm...

TIA

---

### Post by sydnei.lucchesi on 2010-08-15
#cd /
#sudo find -name gdm.conf
./etc/dbus-1/system.d/gdm.conf
./etc/init/gdm.conf
#

---

### Post by bohemier on 2010-08-15
I found a great tutorial to create a vnc-based login server: [http://oapeon.blogspot.com/2010/05/ubuntu-1004-vnc-based-login-server.html](http://oapeon.blogspot.com/2010/05/ubuntu-1004-vnc-based-login-server.html)

Works well for me... as for security, it doesn't metter much in my case since this is on a private network.

HTH

---

