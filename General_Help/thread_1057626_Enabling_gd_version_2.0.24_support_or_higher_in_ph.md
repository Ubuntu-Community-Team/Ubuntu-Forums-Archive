---
title: "Enabling gd version 2.0.24 support or higher in php?"
date: 2009-02-02
forum: General Help
---

### Post by sameer.tahseen on 2009-02-02
Hi Friends, I am a new commer to Ubuntu and as well to ubuntu forums. 
The problem i faced is that i wanted to install a plugin (gk photoslide 2) to joomla on my localserver. When i checked it's system requirements, it said, **gd disabled**. 
I ran the command:
apt-get install php5-gd. and restarted my apache server. 
But the problem persisted, it said, 
A 2.0.1 or higher gd version required. your gd version is not compatible. 
Please help me out, i urgently need to solve this problem. 

my system: 

Acer TravelMate 2420
Webserver: apache2
php version: 5. something
mysql server and client 5.0 
Operating System: Ubuntu 8.10 

Thanks in Advance:popcorn:

---

### Post by sameer.tahseen on 2009-02-02
> **sameer.tahseen said:**
> Hi Friends, I am a new commer to Ubuntu and as well to ubuntu forums. 
The problem i faced is that i wanted to install a plugin (gk photoslide 2) to joomla on my localserver. When i checked it's system requirements, it said, **gd disabled**. 
I ran the command:
apt-get install php5-gd. and restarted my apache server. 
But the problem persisted, it said, 
A 2.0.1 or higher gd version required. your gd version is not compatible. 
Please help me out, i urgently need to solve this problem. 

my system: 

Acer TravelMate 2420
Webserver: apache2
php version: 5. something
mysql server and client 5.0 
Operating System: Ubuntu 8.10 

Thanks in Advance:popcorn:

Isnt there anyone to help me out?????????

---

### Post by simion314 on 2009-02-02
> **sameer.tahseen said:**
> Isnt there anyone to help me out?????????

Search in synaptic and see what version do you have and if it is old, try to google for how to setup on your ubuntu version the setup you need, if you need the latest version and in ubuntu is one older then you must compile it from source.

---

### Post by roycrom on 2009-06-30
It doesn't seem to me that the version in synaptic has changed for a couple of years - it's also difficult to ascertain what version of gd is supplied through the php5-gd package as it is not versioned with the GD version number.

I have installed the latest php5-gd package and it looks like the version is greater than 2 (according to phpinfo), but a package I'm installing does a check and states that it is less than 2.0.1 (which suggests 2.0 is the version installed) however, could the ubuntu package be reporting in a none standard way, making non-ubuntu version checks fail?

---

