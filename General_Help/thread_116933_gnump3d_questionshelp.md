---
title: "gnump3d questions/help"
date: 2006-01-13
forum: General Help
---

### Post by shawnzyoo on 2006-01-13
when on my LAN (another computer) using gnump3d
i can't access my media
but when i m on the server i can access it fine through gnump3d
i am honestly not sure how to even access it from an outside computer
i mean i know just use the url  http://localhost:<port>
is there someting that i have to enable on my router to complete this?
thanks

---

### Post by Appolusionist on 2006-01-13
[quote=shawnzyoo]when on my LAN (another computer) using gnump3d
i can't access my media
but when i m on the server i can access it fine through gnump3d
i am honestly not sure how to even access it from an outside computer
i mean i know just use the url  http://localhost:<port>
is there someting that i have to enable on my router to complete this?
thanks[/quote]

Take a look at your /etc/gnump3d/gnump3d.conf file? I am curious to know what you have listed for allowed_clients and denied_clients.

---

### Post by shawnzyoo on 2006-01-14
here is part of my gnump3d.conf
i am also not sure if i should change things like the host name to my server address?
thanks for the help

#  Only people on the same subnet, (class C):
# allowed_clients = 192.168.2.0/8
#
#  People on the same class B:
# allowed_clients = 10.0.0.0/16
#
#  Only one person:
# allowed_clients = 192.168.2.12
#
#  Everybody
# allowed_clients = all
#
#  Nobody (!)
# allowed_clients = none
#
#  Everybody local, and one remote address:
# allowed_clients = 192.168.2.0/8; 194.247.82.33
#
#  Everybody local, and one remote range:
# allowed_clients = 192.168.2.0/8; 194.237.82.0/8
#
#
allowed_clients = all

---

### Post by shawnzyoo on 2006-01-15
i got it figured out
the problem was with my router
oh well
thanks anyways

---

### Post by magus3498 on 2006-05-13
I'm having the exact same problem. What do I have to do to my router to get it to work on non-server computers?

---

### Post by shawnzyoo on 2006-05-17
you have to set up your router to port forward the correct ports for the gnump3d server
also make sure it is on
sudo /etc/init.d/gnump3d start

---

### Post by saj0577 on 2007-09-06
When on another computer use [http://[computer](http://[computer) internal ip]:8888/  and it will work so for example for my computer it is [http://192.168.0.14:8888/](http://192.168.0.14:8888/)  to access it from a computer not in your network you need to setup port forwarding.

Saj

---

### Post by tgalati4 on 2007-09-06
Log into your router (typically [http://192.168.1.1](http://192.168.1.1))
Set up port forwarding for your server IP and Port number (say 192.168.1.114 and Port 9000)
Test from outside of your network:

[http://wofmusic.homelinux.org:9000](http://wofmusic.homelinux.org:9000)

---

### Post by saj0577 on 2007-09-06
> **tgalati4 said:**
> Log into your router (typically [http://192.168.1.1](http://192.168.1.1))
Set up port forwarding for your server IP and Port number (say 192.168.1.114 and Port 9000)
Test from outside of your network:

[http://wofmusic.homelinux.org:9000](http://wofmusic.homelinux.org:9000)

YOu have just over 1000 songs and it loads real fast i have 10,000 songs is their anyway to make it load as fast as yours?

Saj

---

### Post by tgalati4 on 2007-09-06
I'm not sure how to improve the performance of gnump3d since it is really just a large PERL script.  As the database grows, it will become slower.  I'm using a 1GHz Celeron with a business-grade DSL line for connectivity (2,200 mbits/sec download, I'm not sure of the upload speed).

There are other mp3 serving solutions--most use mysql to create a music database.  Then you might as well set up a full-blown LAMP (or XAMP) server.  I would assume this has better performance.

With gnump3d and its flat-file index system, I would expect a 10X longer load time with 10,000 songs vs 1,000.  Why don't you do some timing tests and let us know what you find?

Long load times are bothersome, but I keep 15 browser tabs open at any one time, so I'm not bothered by slow-loading pages.  It really depends on how it is going to be used.

---

