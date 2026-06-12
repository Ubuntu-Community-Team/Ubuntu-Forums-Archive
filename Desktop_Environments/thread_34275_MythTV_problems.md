---
title: "MythTV problems"
date: 2005-05-14
forum: Desktop Environments
---

### Post by Heliode on 2005-05-14
Hey,

For a while now i've been trying to get MythTV to work. I allready have my remote control working, as well as my tv-tuner (works fine with tvtime). I've followed a couple of howto's but I always get stuck at a certain point. 

This is one of the howto'a i've tried:
[http://www.cs.rit.edu/~css8044/?q=mythtv](http://www.cs.rit.edu/~css8044/?q=mythtv) 

I followed the parts of the howto that applied to me (I already have a working Ubuntu system and my tv-tuner already works, so there are some steps in there I don't need), but I get stuck at [Installing MythTV](http://www.cs.rit.edu/~css8044/?q=mythinstall#) 
The problem seems to be with the database. When I use the command
```

mysql> UPDATE user SET password=PASSWORD('mythtv') WHERE user="mythtv";

```
It returns 
```

Query OK, 0 rows affected (0.13 sec)
Rows matched: 0  Changed: 0  Warnings: 0

```
 When trying to start the mythtv-backend later, it gives me database errors. 

I'm completely lost here. Any suggestions would be extremely welcome!

---

### Post by Heliode on 2005-05-15
A little bit more info...

When I install mythtv, it gives me this:

```

Instaling mythtv-backend (0.17-3) ...
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

```

Just thought that might help. Any thoughts at all? Thanks in advance!

---

### Post by ludi on 2005-05-15
[QUOTE=Heliode]A little bit more info...

When I install mythtv, it gives me this:

```

Instaling mythtv-backend (0.17-3) ...
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

```

Just thought that might help. Any thoughts at all? Thanks in advance![/QUOTE]
 I think that you have to build your DB first and get the rights permissions, but I little confused now.
I remember that I've had a similar problem but I don't know how I fixed ...
Go to [http://www.mythtv.org/](http://www.mythtv.org/) and read the docs. Propably there is a answer to your question there.

---

