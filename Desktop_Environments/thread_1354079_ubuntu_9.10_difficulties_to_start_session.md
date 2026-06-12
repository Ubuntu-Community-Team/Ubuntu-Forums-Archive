---
title: "ubuntu 9.10 difficulties to start session"
date: 2009-12-13
forum: Desktop Environments
---

### Post by teodosio on 2009-12-13
Hi everybody!

I did an up-grade from Ubuntu 9.04 to 9.10. Everything was running nicely until one day there was a power failure while I was working. Since then the Ubuntu asks me to log in with your user name and password. I enter the data, but it doesn't take me to the desktop. Instead I am asked again for the password and so on. Sometimes I have to enter a password more than ten times before I get access to the desktop, other times I have to access through an xterm session from the command line. When I finally get into the desktop, a message appears with this information: (in Portuguese)

"An error occurred while reading or writing configuration information to evolution-alarm-notify. Some of your configuration settings may not work correctly."

When I click on "details" the following  appears:

"Failed to contact configuration server; some possible causes are that you need to enable services to TCP / IP networking for ORBit, or NFS has exclusive rights derived from a system crash. [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) to See more information. (Details - 1: Failed to get connection to session: Failed to connect to socket / tmp / dbus-KgfaPDeOto: Connection refused) "

Someone can help me to solve this? I've been on that gnome site but I did not realize what to do. Frankly, I'm sick of googling and not finding a solution. Thanks everyone in advance
Happy season to all.

---

### Post by teodosio on 2009-12-26
I found the answer in this Forum. :) Just did like this and it worked:

sudo apt-get clean - to clean

sudo apt-get install ubuntu-desktop - to install the Ubuntu Desktop

sudo apt-get update && sudo apt-get upgrade - to update and upgrade package

sudo apt-get -f install - to repair broken packages if necessary

Thank you to the user I can't remember the name...


> **teodosio said:**
> Hi everybody!

I did an up-grade from Ubuntu 9.04 to 9.10. Everything was running nicely until one day there was a power failure while I was working. Since then the Ubuntu asks me to log in with your user name and password. I enter the data, but it doesn't take me to the desktop. Instead I am asked again for the password and so on. Sometimes I have to enter a password more than ten times before I get access to the desktop, other times I have to access through an xterm session from the command line. When I finally get into the desktop, a message appears with this information: (in Portuguese)

"An error occurred while reading or writing configuration information to evolution-alarm-notify. Some of your configuration settings may not work correctly."

When I click on "details" the following  appears:

"Failed to contact configuration server; some possible causes are that you need to enable services to TCP / IP networking for ORBit, or NFS has exclusive rights derived from a system crash. [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) to See more information. (Details - 1: Failed to get connection to session: Failed to connect to socket / tmp / dbus-KgfaPDeOto: Connection refused) "

Someone can help me to solve this? I've been on that gnome site but I did not realize what to do. Frankly, I'm sick of googling and not finding a solution. Thanks everyone in advance
Happy season to all.

---

