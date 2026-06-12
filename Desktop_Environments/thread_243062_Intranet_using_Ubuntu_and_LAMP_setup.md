---
title: "Intranet using Ubuntu and LAMP setup"
date: 2006-08-24
forum: Desktop Environments
---

### Post by sefs on 2006-08-24
Hi all I need a quick bit of advice.

I want to set up an intranet for a small group of users in a windows environment.  I want to install VMWare Server on the Windows Server and install Ubuntu inside the VMWare and configure it with a LAMP setup.

They are the two flavors of ubuntu, desktop and server.   I really want the option of having a gui available as opposed to just having a command line.  So would it be a bad thing to use the desktop setup instead for the "Server". I could probably install all the stuff I dont need as the server will just be serving up a Joomla website to an internal network.

Also can I use Xubuntu as opposed to Ubuntu? Any problems with that?

Thanks.

---

### Post by dmeehan on 2006-08-25
I have Xubuntu desktop acting as a webserver for my home network. I use Xampp as the webserver which is fine for php & mysql stuff that i am using.

Xampp is really easy to setup, you just unzip it and start it...

---

### Post by Woei on 2006-08-25
> **sefs said:**
> Hi all I need a quick bit of advice.

I want to set up an intranet for a small group of users in a windows environment.  I want to install VMWare Server on the Windows Server and install Ubuntu inside the VMWare and configure it with a LAMP setup.

They are the two flavors of ubuntu, desktop and server.   I really want the option of having a gui available as opposed to just having a command line.  So would it be a bad thing to use the desktop setup instead for the "Server". I could probably install all the stuff I dont need as the server will just be serving up a Joomla website to an internal network.

Also can I use Xubuntu as opposed to Ubuntu? Any problems with that?

No, no problem at all. The only difference between the various flavors of Ubuntu is the default set of packages that will be installed at installation time. For any given flavor of Ubuntu, you generally can morph it into another one through the power of the dpkg package system.

Moreover, there's nothing stopping you from installing webservers, database servers, programming tools or whatever on any Ubuntu system. You can pick and match any software in the various repositories of software you like -- within the constraints of what's technically possible of course, some packages simply conflict because they provide the same set of files. So yes, you're free to install Xubuntu, and run Apache/LightHTTP, a database like MySQL or PostgreSQL and any PHP based CMS like Joomla.

Please note that performance, especially I/O throughput, will not be optimal due to the inherent inefficiencies of a full virtualization solution like VMWare.

---

### Post by az on 2006-08-25
> **sefs said:**
> Hi all I need a quick bit of advice.

I want to set up an intranet for a small group of users in a windows environment.  I want to install VMWare Server on the Windows Server and install Ubuntu inside the VMWare and configure it with a LAMP setup.

They are the two flavors of ubuntu, desktop and server.   I really want the option of having a gui available as opposed to just having a command line.  So would it be a bad thing to use the desktop setup instead for the "Server". I could probably install all the stuff I dont need as the server will just be serving up a Joomla website to an internal network.

Also can I use Xubuntu as opposed to Ubuntu? Any problems with that?

Thanks.

Nothing prevents you from installing the LAMP stack on a desktop system, other that going against best security practices.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

It's a lot easier to just install apache2 php5-mysql libapache2-mod-php5 mysql-server from an Ubuntu/Kubuntu or Xubuntu install than XAMMPP.

To install Joomla on Ubuntu:
[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

---

### Post by TravisNewman on 2006-08-25
FYI, I have installed egroupware for my company's intranet portal and it's fantastic!

---

### Post by sefs on 2006-08-27
I stand amazed that this product can be free.

> **panickedthumb said:**
> FYI, I have installed egroupware for my 
company's intranet portal and it's fantastic!

---

