---
title: "Serial autoconfig"
date: 2006-06-20
forum: Desktop Environments
---

### Post by johndoe2008 on 2006-06-20
Hey,

Not sure if this is the right forum for this, but I'm not sure where else it could go.
I am trying to find the setserial autoconfig file. The setserial info pages say that there is supposed to be a /etc/serial.conf file, but I cant seem to find it. I am using Ubuntu 6.06 i386 desktop version. Could anyone instruct me at to what file I need to change so that I don't need to rerun setserial everytime I restart?

Thank you

---

### Post by lamego on 2006-06-20
The setserial package doest install an /etc/init.d/serial boot script that will check for the configuration file /etc/serial.conf .

Here is an example file that you can use:
[http://ftp.debian.org/doc/setserial/serial.conf](http://ftp.debian.org/doc/setserial/serial.conf)

---

### Post by johndoe2008 on 2006-06-20
Got it to work, thanks for the help.

---

### Post by Ptero-4 on 2006-08-14
Hi. I used your serial.conf file and wanted to know. Why pppconfig/pon isn't seeing the modem? pppd complains that it can't get the terminal parameters and closes.

---

