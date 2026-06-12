---
title: "is there a fire wall installed on ubuntu"
date: 2006-01-19
forum: General Help
---

### Post by njzillest on 2006-01-19
is there a firewall on ubuntu, and if there is how and where can i acess it?

---

### Post by drfalkor on 2006-01-19
There is no need for a firewall ( I dont use it) - but if you want you can install firestarter..

sudo apt-get install firestarter

-have fun :KS

---

### Post by majed on 2006-01-19
most people say you don't need one on a fresh ubuntu.. but i use firestarter just to feel safer :)

---

### Post by frodon on 2006-01-19
Ubuntu include embedded firewall (ipchain, iptables), but if you're not used to ipchain and iptable i advice you firestarter (like drfalkor and majed) which is a frontend for iptable and ipchain.
Firestarter website : [http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by AmboyGuy on 2006-01-19
There is also this thread: [[url=http://ubuntuforums.org/showthread.php?t=50014] ]("http://ubuntuforums.org/showthread.php?t=50014")[** 	New Firewall Script For Ubuntu]("http://ubuntuforums.org/showthread.php?t=50014")**[/URL]
 []("http://ubuntuforums.org/showthread.php?t=50014")

---

### Post by bulldogzerofive on 2006-01-19
You do not need a firewall for a stand alone system.  In *nix, if there is no service listening to a port that port is simply closed.  You do, however, need to know what services are listening to ports and make sure that those services are themselves secure.

Enter this into a terminal:

```
sudo netstat -tulp
```

Be sure the window is wide enough that the text does not wrap around and look like garbage.  You should get a quick rundown of all services that are listening to ports on your system.  

For example, this is what I get:

```
user@localhost:~$ sudo netstat -tulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost.localdo:32769 *:*                     LISTEN     8581/hpiod
tcp        0      0 localhost.localdo:32770 *:*                     LISTEN     8600/python
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     8551/cupsd
tcp        0      0 localhost.localdom:smtp *:*                     LISTEN     8716/exim4
udp        0      0 *:bootpc                *:*                                7683/dhclient3
user@localhost:~$
```


These are all on loopback, meaning that they are only listening to the computer itself; with a default ubuntu install, it should be nothing but cupsd (print server) and exim4 (system internal mail server), I think, all of which are on loopback and not actually listening to the internet.  When something does show up there (if for example you want to install a web server, it will obviously show up on port 80), do your research on it (ask here if you need to; there are very helpful people here), and make sure that that service is running in a way that does not compromise your security.  You should probably check back with netstat each time you install anything with "server" anywhere in the name or description or if you install large meta-packages.

If you want to forbid certain types of access (like all outbound to forbiddenwebsite.com or all traffic on port 80, say to keep your kids out of certain things on the internet), you can do that with IPtables.  IPtables is difficult to configure; there are some good graphical front ends that will configure it for you like firestarter or (my favorite) guarddog. You can also configure it to log all connections of any kind, if you are paranoid.

Also, if you are looking for the kind of thing that tries to limit outbound internet access on an application-by-application basis like many windows firewalls attempt to do (zone alarm or norton, for example), forget about it.  This does not exist in linux (as far as I know) because there has been no demand to write such a thing.  Besides, these are so easy to subvert for someone or something with root access that they are useless gadgets, really.

---

### Post by njzillest on 2006-01-19
wow thanx alot you guys are great

---

