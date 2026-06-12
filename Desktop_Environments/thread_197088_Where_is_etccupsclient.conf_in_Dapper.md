---
title: "Where is /etc/cups/client.conf in Dapper?"
date: 2006-06-15
forum: Desktop Environments
---

### Post by istoyanov on 2006-06-15
When I recently installed Ubuntu 6.06 (Dapper Drake) on a machine that used to be  client of a CUPS server, I wanted to add the default CUPS server in /etc/cups/client.conf, but I was really surprised when I didn't find the mentioned file (available in any of the previous Ubuntu releases). The CUPS server itself is set-up perfectly -- to use it, all I had to do (until now) was to add its name in (the client's) /etc/cups/client.conf and the shared printer appeared automagically in GNOME CUPS manager (System -> Administration -> Printing).

Here my question: do Dapper still use this file when acting as a CUPS client, or is this configuration option moved somewhere else? Is it deprecated, or should I create this file by myself?

I'd appreciate any hints on how to proceed further!

---

### Post by Keith_Beef on 2006-06-15
[QUOTE=istoyanov]When I recently installed Ubuntu 6.06 (Dapper Drake) on a machine that used to be  client of a CUPS server, I wanted to add the default CUPS server in /etc/cups/client.conf, but I was really surprised when I didn't find the mentioned file (available in any of the previous Ubuntu releases). The CUPS server itself is set-up perfectly -- to use it, all I had to do (until now) was to add its name in (the client's) /etc/cups/client.conf and the shared printer appeared automagically in GNOME CUPS manager (System -> Administration -> Printing).

Here my question: do Dapper still use this file when acting as a CUPS client, or is this configuration option moved somewhere else? Is it deprecated, or should I create this file by myself?

I'd appreciate any hints on how to proceed further![/QUOTE]

Strange, because on my system the file is there:

```
$ ls -al /etc/cups/client.conf
-rw-r--r-- 1 root root 2204 2005-09-14 09:47 /etc/cups/client.conf

$ uname -a
Linux sheaf 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
```



Beef.

---

### Post by esisa on 2006-06-15
Same thing on my Dapper machines. No client.conf file. However, it worked just copying an old file from by Breezy Badger machine.

---

### Post by istoyanov on 2006-06-15
Here's a listing of the /etc/cups directory on the machine in question (clean Dapper install):

```
root@ubuntu:~$ ls -l /etc/cups
total 36
-rw-r--r-- 1 root   root 1215 2006-05-03 23:41 command.types
drwxr-xr-x 2 root   root  112 2006-06-15 14:58 cups.d
-rw-r--r-- 1 root   root 2640 2006-05-17 15:46 cupsd.conf
drwxr-xr-x 2 root   root   48 2006-05-17 15:46 interfaces
-rw-r--r-- 1 root   root 4461 2006-05-17 15:46 mime.convs
-rw-r--r-- 1 root   root 6109 2006-05-17 15:46 mime.types
drwxr-xr-x 2 cupsys lp     48 2006-05-17 15:46 ppd
-rw-r--r-- 1 root   root  946 2006-05-03 14:45 pstoraster.convs
-rw-r--r-- 1 root   root  242 2006-05-31 03:55 raw.convs
-rw-r--r-- 1 root   root  213 2006-05-31 03:55 raw.types
```
Can anyone provide a default client.conf for reference?

TIA!!!

P.S. Meanwhile, a friend suggested to search at [http://packages.ubuntu.com](http://packages.ubuntu.com), and it revealed that /etc/cups/client.conf isn't included in any Dapper package, indeed. It looks like I'm going to submit a bugreport on that...

```
Package Contents Search Results

You have searched for client.conf in dapper, architecture i386.
Found 12 matching files/directories, displaying files/directories 1 to 12.

FILE                                                       PACKAGE

etc/afbackup/client.conf				    utils/afbackup-client [universe]
etc/mixmaster/client.conf				    mail/mixmaster [universe]
etc/prelude/default/client.conf				    libs/libprelude2 [universe]
etc/systemimager/client.conf				    admin/systemimager-client [universe]
usr/share/doc/libace-doc/examples/APG/Logging/client.conf   doc/libace-doc [universe]
usr/share/doc/libtao-doc/examples/Quoter/client.conf	    doc/libtao-doc [universe]
usr/share/doc/libtao-doc/examples/RTCORBA/Activity/client.conf doc/libtao-doc [universe]
usr/share/doc/libtao-doc/examples/Simple/time-date/client.conf doc/libtao-doc [universe]
usr/share/doc/libtao-orbsvcs-dev/examples/Notify/Lanes/client.conf libdevel/libtao-orbsvcs-dev [universe]
usr/share/doc/libtao-orbsvcs-dev/examples/Notify/ThreadPool/client.conf libdevel/libtao-orbsvcs-dev [universe]
usr/share/doc/libtao-orbsvcs-dev/examples/Security/Send_File/client.conf libdevel/libtao-orbsvcs-dev [universe]
usr/share/doc/openvpn/examples/sample-config-files/client.conf net/openvpn [universe]
```

---

### Post by viernes-rock on 2006-06-15
What is Ubuntu? How does it work?

---

### Post by esisa on 2006-06-15
[QUOTE=istoyanov]Here's a listing of the /etc/cups directory on the machine in question (clean Dapper install):

Can anyone provide a default client.conf for reference?

TIA!!![/QUOTE]

This is my client.conf file:

```
#
#
#   Sample client configuration file for the Common UNIX Printing System
#   (CUPS).
#
#   Copyright 1997-2005 by Easy Software Products, all rights reserved.
#
#   These coded instructions, statements, and computer programs are the
#   property of Easy Software Products and are protected by Federal
#   copyright law.  Distribution and use rights are outlined in the file
#   "LICENSE.txt" which should have been included with this file.  If this
#   file is missing or damaged please contact Easy Software Products
#   at:
#
#       Attn: CUPS Licensing Information
#       Easy Software Products
#       44141 Airport View Drive, Suite 204
#       Hollywood, Maryland 20636 USA
#
#       Voice: (301) 373-9600
#       EMail: cups-info@cups.org
#         WWW: http://www.cups.org
#

########################################################################
#                                                                      #
# This is the CUPS client configuration file.  This file is used to    #
# define client-specific parameters, such as the default server or     #
# default encryption settings.                                         #
#                                                                      #
########################################################################

#
# ServerName: the hostname of your server.  By default CUPS will use the
# hostname of the system or the value of the CUPS_SERVER environment
# variable.  ONLY ONE SERVER NAME MAY BE SPECIFIED AT A TIME.  To use
# more than one server you must use a local scheduler with browsing
# and possibly polling.
#

#ServerName myhost.domain.com
ServerName idunn

#
# Encryption: whether or not to use encryption; this depends on having
# the OpenSSL library linked into the CUPS library.
#
# Possible values:
#
#     Always       - Always use encryption (SSL)
#     Never        - Never use encryption
#     Required     - Use TLS encryption upgrade
#     IfRequested  - Use encryption if the server requests it
#
# The default value is "IfRequested".  This parameter can also be set
# using the CUPS_ENCRYPTION environment variable.
#

#Encryption Always
#Encryption Never
#Encryption Required
#Encryption IfRequested


#
#

```

---

### Post by istoyanov on 2006-06-15
[SIZE="4"]Huge[/SIZE] thanks, **esisa**, for providing a client.conf!!!

Cheers!!!:D

---

