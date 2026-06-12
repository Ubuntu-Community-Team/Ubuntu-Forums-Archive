---
title: "MythTV remote frontend will not connect"
date: 2008-08-19
forum: Desktop Environments
---

### Post by lintoon on 2008-08-19
I have an ubuntu 8.04 "server" which is running Mythtv backend and frontend.
The frontend works fine and I can watch TV on the "server".

I would like to be able to run the frontend on my laptop over my home lan but am unable to.
When I launch the frontend from the Applications menu nothing happens.
When I type "mythfrontend" in terminal I get the following and it just sticks there:

2008-08-18 22:14:36.083 Using runtime prefix = /usr, libdir = /usr/lib
QServerSocket: failed to bind or listen to the socket
2008-08-18 22:14:36.085 MediaRenderer::HttpServer Create Error
2008-08-18 22:14:36.093 XScreenSaver support enabled
2008-08-18 22:14:36.094 DPMS is active.
2008-08-18 22:14:36.094 Empty LocalHostName.
2008-08-18 22:14:36.094 Using localhost value of Toshub
2008-08-18 22:14:36.095 Testing network connectivity to 192.168.1.7
2008-08-18 22:14:36.129 New DB connection, total: 1

/etc/mythtv/mysql.txt has the same user details as the "server". 
The details in /etc/mythtv/mysql.txt and ~/.mythtv/mysql.txt are identical.
I have set "DBHostName" to the ip address of my backend on both systems.
I have commented out the bind to address in /etc/mysql/my.cnf on the server.
I have set mysql to allow connections from 192.168.1.%
The port is set to 6543 within mysql.txt on both systems. Is that right??

Thank you.

---

### Post by lintoon on 2008-08-19
When I restart mythtv backend I get this:

sudo /etc/init.d/mythtv-backend restart
 * Restarting MythTV server: mythbackend
QSettings: error creating /home/mythtv/.qt

also

When I set mysql to allow network connections I was only able to get access by typing:

sudo mysql -h 127.0.0.1 -p mythconverg

Then I pressed enter to make sure no password was set (as seen in lots of posts).  I was then at the mysql prompt.

I tried many other ways to connect but they give the following error:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

I think I'm going crazy and I'm sick of drinking coffee.  The cans are coming out soon :)

---

### Post by lintoon on 2008-08-19
Update:  It's working.  Here's how for anyone interested.

On the backend system I ran:

sudo killall mythtv-backend
then 
sudo /etc/init.d/mythtv-backend start

On the remote frontend I ran

mythfrontend

This launched setup so I confirmed my settings and clicked next a few times and now I can watch TV on my laptop on the lan.  When I quit the frontend I mistakenly selected exit and shutdown.  This shutdown my laptop and when I logged back in it was still working.  Fantastic.

Now I just have to restart the backend pc and see what happens.  I'll post the results.

---

### Post by lintoon on 2008-08-19
I've rebooted the backend pc and it's still working.

---

