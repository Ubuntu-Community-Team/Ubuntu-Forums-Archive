---
title: "Teamspeak 3 server will not start"
date: 2012-11-14
forum: Gaming &amp; Leisure
---

### Post by QsoftStudios on 2012-11-14
Im not sure if I am putting this in the right place so I apologize in advance to the admins if its not. Im having a bit of an issue starting up my TS3 server. Here is what happens.
```
kevin@QsoftStudios:~/teamspeak$ sh ts3server_startscript.sh start
ts3server.pid found, but no server running. Possibly your previously started server crashed
Please view the logfile for details.
Starting the TeamSpeak 3 server
TeamSpeak 3 server started, for details please view the log file
kevin@QsoftStudios:~/teamspeak$ Inconsistency detected by ld.so: dl-version.c: 230: _dl_check_map_versions: Assertion `needed != ((void *)0)' failed!

```

Any ideas? Im running Ubuntu 11.10 server edition x86

---

### Post by Am Elder on 2012-11-14
I've never used Teamspeak, but I might be able to help with a few obvious questions, after doing an internet search for your error.  Have you done a checksum of the package you used to install Teamspeak?  It might be corrupt.  Also, check to make sure you have all the dependencies installed.

Someone else here might be able to help you better, or you might try the [Teamspeak forums]("http://forum.teamspeak.com/forumdisplay.php/108-Linux-FreeBSD").

---

### Post by QsoftStudios on 2012-11-14
> **Am Elder said:**
> I've never used Teamspeak, but I might be able to help with a few obvious questions, after doing an internet search for your error.  Have you done a checksum of the package you used to install Teamspeak?  It might be corrupt.  Also, check to make sure you have all the dependencies installed.

Someone else here might be able to help you better, or you might try the [Teamspeak forums]("http://forum.teamspeak.com/forumdisplay.php/108-Linux-FreeBSD").

I have done both and its still not working

---

### Post by vandorjw on 2012-11-15
why did you not intstall Teamspeak via the Ubuntu Repositories?

sudo apt-get install teamspeak-client

---

### Post by QsoftStudios on 2012-11-15
Its not there, plus I have always just downloaded the tar from the website and run the sh file.

---

### Post by Am Elder on 2012-11-15
I assume you've walked through the [Teamspeak with MySQL tutorial]("http://forum.teamspeak.com/showthread.php/74883-TUTORIAL-Teamspeak3-Server-w-MySQL-Databse-on-Debian-Ubuntu") in the Teamspeak support forums?  I just d/l-ed and unpacked the tar from the website and it worked right off the bat for me on 12.10 just fine.

---

### Post by QsoftStudios on 2012-11-15
> **Am Elder said:**
> I assume you've walked through the [Teamspeak with MySQL tutorial]("http://forum.teamspeak.com/showthread.php/74883-TUTORIAL-Teamspeak3-Server-w-MySQL-Databse-on-Debian-Ubuntu") in the Teamspeak support forums?  I just d/l-ed and unpacked the tar from the website and it worked out of the box for me on 12.10 just fine.

Yes I have if set up teamspeak a number of times. I dont think its a SQL error from what is outputed when I start the server.

```
Inconsistency detected by ld.so: dl-version.c: 230: _dl_check_map_versions: Assertion `needed != ((void *)0)' failed!
```

It looks like a C library issue but im not quite sure how to fix it.

---

### Post by QsoftStudios on 2012-11-18
Never mind I got it working.

---

### Post by fuad121 on 2012-12-31
Please anybody tell me how I learn good Teamspeak 3 server. I will be a server expert . How i learn it. I am new here. Some times I fell This is not possible. I have no hues knowledge in server.

---

