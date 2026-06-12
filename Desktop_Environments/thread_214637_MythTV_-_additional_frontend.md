---
title: "MythTV - additional frontend"
date: 2006-07-12
forum: Desktop Environments
---

### Post by crazydahveed on 2006-07-12
Ok, so here is my setup.  I have an Ubuntu box that is currently running MythTV backend and frontend (and working great).  I am wanting to add the MythTV frontend to another machine (an iMac) and connect it to the backend of the first.  

Every time I launch the front end on the iMac, it prompts for the connection information after failing to connect to mySQL.  I have setup the backend to host off its IP address rather than the localhost address, and set the iMac to point to that address.  When I setup the Ubuntu box using the mySQL username of root with a blank password, but when I went to check it later on, it had changed it to the "mythtv" user with a random password entered.

I tried every username/password combo I could think of on the iMac (root, mythtv), but it does not seem to be working.  Do I have to do some sort of setup to allow remote connections on mySQL/MythTV?  

I would greatly appreciate any assistance you can provide.  This is my first time doing networking related functions on the Ubuntu box.

---

### Post by challahc on 2006-07-12
Did you change mysql to listen on the ip not localhost?

in /etc/mysql/my.cnf
change the bind-address setting
bind-address            = 127.0.0.1

change 127.0.0.1 to ip of box

restart mysql

---

### Post by challahc on 2006-07-12
also, the mythtv password used at install is stored in /etc/mythtv/mysql.txt

---

### Post by crazydahveed on 2006-07-12
Ok, I set the bind-address to the computers IP, and apparently there was a kernel update, so I had to rebuild the ivtv drivers.  but after doing that, I still cannot connect to the mySQL database from the Mac.  It works fine on the local machine, but the Mac still cannot connect to the mySQL database.  Is there a program I can run to test the mySQL database connection?  Also, do I have to do something to allow the root account to connect using a blank password (by the way, is this just a mySQL account)?  I have to be up early for work, so I will check this again tomorrow for comments.  Thanks challahc for your help so far!

---

### Post by crazydahveed on 2006-07-15
Ok, here is what I have done:

1. Commented out the bind-address from the my.cnf
2. Ran the following command in mysql (let me know if it is wrong, I updated it for my use):
     grant all on mythconverg.* to root@"192.168.0.%" identified by "";
     flush privileges;
3. Set the mythtv backend to run on 192.168.0.9 (backend IP).
4. Set the Mac to look for the database on 192.168.0.9.

Now I am getting access denied for root@"192.168.0.7" (Mac IP).  What am I doing wrong?  It is obviously trying to connect, and I know the password is correct as it is blank.  Can anyone offer me some assistance as to why I cannot connect to the mySQL database?  This is driving me insane.

---

### Post by crazydahveed on 2006-07-17
Well, I now have it up and running.  I am not entirely sure as to why it would not connect with the previous settings; however, when I used the mythtv username and password, everything worked (I had also set this information in mysql).  Thanks again.  I hope this can help someone in the future.

---

