---
title: "Cedega Help"
date: 2006-04-25
forum: Gaming &amp; Leisure
---

### Post by SolidSnake2 on 2006-04-25
Hi, Im having alot of trouble with launching Cedega on Ubuntu. I downloaded the free trial tomy desktop, but when I double click it to lanuch it, it says something along the lines of" you must choose the code type so its not binary".Does anyone have any idea what to do?

---

### Post by conedude13 on 2006-04-25
try starting up cedega through a terminal window.  From the directory where the download is, type in "sudo sh cedega_timedemo_installer" and then your password.

Once it is done installing, you can just type in "sudo cedega_timedemo" from any directory to start it up.

(helpful readme [HERE](http://downloads.transgaming.com/files/timedemo_howto.html))

---

### Post by NXArmada on 2006-04-26
If you read the demo [HOW TO]("http://downloads.transgaming.com/files/timedemo_howto.html") on the transgamin it well tell you what to do.

**Installation**

The Cedega Time Demo can be installed in one of two ways: system wide for all users or on a per user basis. In either case, games will be installed to: /PATH_TO_INSTALLATION/.cedega_timedemo. Be sure that the Time Demo is installed into a location with enough space for games.
Shared System Wide Installation

As root run the installation package using:

# sh /PATH_TO_INSTALLER/cedega_timedemo_installer

When installing on a system wide basis all users will have the ability to run the Time Demo, install and play games. All installed games will be available to all users on the system.
Per User Basis

As a non-root user run the installation package using:

$ sh /PATH_TO_INSTALLER/cedega_timedemo_installer

When installing the Time Demo as a non-root ,the files may only be installed into a location that the user has write permissions to. Only the user that installs the Time Demo will be able to run it and have access to games installed through Cedega. The default location for the installation is the users home directory.
Post Installation

After the installation is complete users will need to register the Time Demo. Fill in the registration form and press submit (a live Internet connection is required for this step). Shortly after submitting the registration information an email will be sent back to the user containing a registration key. Enter the registration key to connect to a server and start the Time Demo (a live Internet connection is required for this step). 

**How to Start the Time Demo**
System Wide (Using Default Installation Settings)

Using the default installation settings the Time Demo can simply be started using:
$ cedega_timedemo

or using

$ /usr/local/bin/cedega_timedemo
Per User Basis (Using Default Installation Settings)

Using the default installation settings the Time Demo can simply be started using:

$ ~/cedega_timedemo

---

### Post by siorai on 2006-04-26
[QUOTE=conedude13]try starting up cedega through a terminal window.  From the directory where the download is, type in "sudo sh cedega_timedemo_installer" and then your password.

Once it is done installing, you can just type in "sudo cedega_timedemo" from any directory to start it up.

(helpful readme [HERE](http://downloads.transgaming.com/files/timedemo_howto.html))[/QUOTE]
I don't think you really need to or would even want to run it as root. It will run fine as the normal user.

---

