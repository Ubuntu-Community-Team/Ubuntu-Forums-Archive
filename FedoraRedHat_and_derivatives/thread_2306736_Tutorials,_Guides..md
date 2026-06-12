---
title: "Tutorials, Guides."
date: 2015-12-18
forum: Fedora/RedHat and derivatives
---

### Post by ex-para on 2015-12-18
The Linux Daily
Tutorials, Guides, Tips, and Tricks from Everyday Experiences
Procedure:
1.) Install the software:
The following command will install the programs needed for HTTPD (PHP enabled) called Apache and PHP. These programs are the heart of the web server. Just type or copy/paste them into the terminal.
yum install php httpd system-config-httpd mod_ssl
chkconfig httpd on
service httpd restart
The configuration of the web server by default will be fine for most users, but if you’d like to make it your own, the files are located here:
/etc/php.ini
/etc/httpd/conf/*
/etc/httpd/conf.d/*

I tried this in terminal but it does not work and I wonder why. I have yum and what ever else installed so this is as far as I got.

---

### Post by sudodus on 2015-12-18
Why are you using yum? The corresponding program in Ubuntu is apt-get.

I'm not sure that it is enough to install yum to get all the infrastructure you need: are there program packages made for yum in the Ubuntu repositories?

---

### Post by slickymaster on 2015-12-18
Assuming the OP is not sitting on *buntu box, I'm moving the thread to the **Fedora/RedHat and derivatives** sub-forum

---

### Post by ex-para on 2015-12-18
The tutorial tells me to use it. What is the corresponding program? Thanks for the reply.

---

### Post by howefield on 2015-12-18
Exactly which operating system are you using, and is [this]("http://www.thelinuxdaily.com/2008/01/tutorial-setup-your-own-self-hosted-simple-web-server-for-free/") the tutorial you are referring to  ?

---

### Post by ex-para on 2015-12-18
Correct.

---

### Post by sudodus on 2015-12-18
Please tell us which operating system you are using - I assumed Ubuntu, but if you use another system, the advice will be different.

---

### Post by howefield on 2015-12-18
I'll ask again, which operating system are you running, getting blood out of a stone comes to mind.

The tutorial you are following was made for Fedora 8 which is a somewhat old version to say the least, Fedora are now on version 23 or 24, can't remember. That's not to say it won't work but you may want to find a more current tutorial and one which fits the actual system that you are running.

---

### Post by ex-para on 2015-12-18
I thought I had replied, yes the one you show is the one and I am using Ubuntu 12  Lts. Thanks for the replies.

---

### Post by brian-mccumber on 2015-12-18
This is a much easier tutorial for installing a lamp server on Ubuntu. It may work with 12 since it's supported until 2017, but I don't know I installed it on 14.04.

[http://howtoubuntu.org/how-to-install-lamp-on-ubuntu](http://howtoubuntu.org/how-to-install-lamp-on-ubuntu)

---

### Post by ex-para on 2015-12-19
Thank you. but I also need the bit that gets the site on the Web if that is possible. I have nginx at the moment and I host myself but I have reasons to wish to change.

---

### Post by ex-para on 2015-12-19
I think I may have found the bit i need.

---

