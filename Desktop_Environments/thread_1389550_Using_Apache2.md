---
title: "Using Apache2"
date: 2010-01-24
forum: Desktop Environments
---

### Post by pacart on 2010-01-24
As I am new to using a Linux os, I am having a little trouble but am slowly getting the hang of things.

I have installed lamp server on my ubuntu 9.10 desktop enviroment.

Could someone tell me how to modify and save the apache2/default file.
I tried sudo vim /etc/apache2/sites-available/default

It works and I can edit the file but I don't know how to save it.
Thanks in advance.

---

### Post by jbiggs12 on 2010-01-24
I don't know about vim, but you can always try gedit or nano.

```
sudo gedit /etc/apache2/sites-available/default
```

---

### Post by pacart on 2010-01-24
Looks like I need to change my permissions to allow me to save it.
This message appears.
**You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again.**

I will try to find out how to chmod  the file or If somebody is willing to tell me how It would be greatly appreciated.

---

### Post by sirko on 2010-01-24
to edit it in terminal
> sudo pico /etc/apache2/sites-available/default
exit with Ctrl+X it will ask you to save it press Y
to change the permission try this, where xxx is your user name
> sudo chown xxx /etc/apache2/sites-available/default or

> sudo chmod 777 /etc/apache2/sites-available/default

---

### Post by pacart on 2010-01-25
> **sirko said:**
> to edit it in terminal

exit with Ctrl+X it will ask you to save it press Y
to change the permission try this, where xxx is your user name
 or
**Thank you all for your help. Information was spot on and worked.:)**

---

### Post by Lars Noodén on 2010-01-25
> **sirko said:**
> to edit it in terminal
```

sudo chmod 777 /etc/apache2/sites-available/default 

```
 or

@ pacart : that advice 'works' but mode 777 gives full read and write access to **anyone** and **everyone** that can find that directory or file.  In other words, it also potentially gives write access to random strangers, including sirko, on the net who might stumble across your web server.  

@ sirko : if you read that 'tip' somewhere, could you please post the URL so that the source document can be fixed?

Setting configuration files so that the server, or others, can edit them allows a bug in your web service (especially PHP scripts) to be used to gain full access, eventually full root access, to the system.  

jbiggs12 has a safe way:

```

# option 1
sudo gedit /etc/apache2/sites-available/default

# option 2
sudo nano /etc/apache2/sites-available/default

# option 3
sudo vim /etc/apache2/sites-available/default

```

Or by itself or in conjunction with the above, you can do the following:

If you want more access you can make a group called 'webmasters', then change the group membership of the directory 'sites-available' and the files in it to 'webmasters' then give write permission to that group.

Then you can allow some or all of the following to that group via sudoers:

```

# in /etc/sudoers

%webmasters ALL=(ALL) PASSWD: /usr/bin/nano /etc/apache2/sites-available/*

%webmasters ALL=(ALL) PASSWD: /usr/sbin/a2enmod, /usr/sbin/a2dismod, \
  /usr/sbin/a2ensite, /usr/sbin/a2dissite, /usr/sbin/apache2ctl, \
  /etc/init.d/apache2


```

---

### Post by sirko on 2010-01-25
Yes the fault is mine 777 is not good idea! chown will work fine and secure or if you prefer you can edit it as root in terminal (or gedit if you rinning GUI)

---

