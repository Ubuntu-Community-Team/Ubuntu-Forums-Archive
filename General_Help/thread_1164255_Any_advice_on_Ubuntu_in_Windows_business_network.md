---
title: "Any advice on Ubuntu in Windows business network"
date: 2009-05-19
forum: General Help
---

### Post by amadeus266 on 2009-05-19
My employer saw my laptop running Ubuntu 8.04 and started asking questions. He also read the article about Ernie Ball (the quitar string maker) and his complete move to open source. As of next month, we are migrating all 12 of our windows xp workstations over to Ubuntu. I have already set up a test machine for everyone to try out and give feedback. This is a Windows 2003 AD network so I am looking for any input as to what I should look out for or stay away from.

---

### Post by kimda on 2009-05-19
Are these co-workers allready experienced with Linux/OpenSource programs? I would recommend implementing it in fases. So starting with firefox instead of Internet Explorer. Change to open office instead of MS office. This will make the change easier since they will be familiar with these programs. Also if you store all your documents in proprietary formats you could get into trouble with Linux/OpenSource since everything is backengineerd. So instead of storing your word documents in word try to save everything in rtf or odt which are more of an open format. Try to make transition as smooth as possible by planning things. Some things won't work under Linux as its an complete different system. For instance certain Microsoft server functionality will not work with Linux. Like roaming profiles. I do not know your level of knowledge but also centralised authentication might be hard to realise. So instead of trying to getting it work with AD i would just add the users/groups locally. I have never done a migration with the workstations first. My suggestion would be try to get everything which is essential to get work done installed on this test machine. And let all these coworkers work on it for maybe a day like you said. After you ironed out the problems migrate the rest. Also document your work. Not only for future references but also for the continuity of the business.

---

### Post by amadeus266 on 2009-05-19
> **kimda said:**
> Are these co-workers allready experienced with Linux/OpenSource programs? I would recommend implementing it in fases. So starting with firefox instead of Internet Explorer. Change to open office instead of MS office. This will make the change easier since they will be familiar with these programs. Also if you store all your documents in proprietary formats you could get into trouble with Linux/OpenSource since everything is backengineerd. So instead of storing your word documents in word try to save everything in rtf or odt which are more of an open format. Try to make transition as smooth as possible by planning things. Some things won't work under Linux as its an complete different system. For instance certain Microsoft server functionality will not work with Linux. Like roaming profiles. I do not know your level of knowledge but also centralised authentication might be hard to realise. So instead of trying to getting it work with AD i would just add the users/groups locally. I have never done a migration with the workstations first. My suggestion would be try to get everything which is essential to get work done installed on this test machine. And let all these coworkers work on it for maybe a day like you said. After you ironed out the problems migrate the rest. Also document your work. Not only for future references but also for the continuity of the business.

Already did Firefox and OpenOffice about 1 year ago now. We don't use roaming profiles so that isn't a problem. I know you can bind a Linux workstation to Active Directory but I haven't tried anything with that yet.

---

### Post by wsonar on 2009-05-19
Wel I'm in an AD enviroment and I find many things challenging

like this

[http://ubuntuforums.org/showthread.php?t=1160456]("http://ubuntuforums.org/showthread.php?t=1160456")

I think openSuse does a little better with AD authentication 

but there will be many challenges less ms solutions the less challenges

the company I work for develops an LIS/BIS system that are heavily driven by IE and .net not to mention they'd rather by an 6000 dollar blade than a better piece of hardware for half the price regardless of OS but that's Corporate America for you.

---

### Post by amadeus266 on 2009-05-20
If AD works at all I will be satisfied. Last time I tried OpenSuse, it seamed to require a lot of overhead on the machine and literally took hours for the install. We only need 2 applications from the win2k3 server (specialised software specific to our industry and no substitute in any OS) and I would like to run them using seamless rdesktop. My test machine was originally set up with 9.04 and had the window border bug. Today I installed 8.04 since that is what I have on my laptop but I failed to realise that Windows networking was broken in that version since I don't actually navigate the network with it . So tomorrow I will go back to 9.04 and just deal with the menus having their own Gnome window borders in order to be able to access the company documents. Is it possible to map special folders like in Windows XP? (i.e. remap the My documents folder to a folder on the server.) It did this in Windows to prevent documents from being spread all over the network. This is just phase 1 of my little project... Phase 2 is PCI DSS compliance. We simply cannot reach PCI DSS compliance with half of our workstations running Window XP Home edition. At least the applications I need to access are already compliant. Just for kicks, since I work for a music store, I think I will try Ubuntu Studio. I will keep posting on my progress. Oh and Kimda, I already document EVERYTHING as I inherited this network from someone who took 3 years to give me a list of 61 different passwords he would use and didn't document anything.


To be continued...

---

### Post by kimda on 2009-05-20
You could mount the "My Documents" with cifs mounts. Just add a line to /etc/fstab:

ex:
//192.168.1.1/documents /home/user/Documents cifs credentials=/root/.cred,_netdev 0 0

In the .cred file:
username=username
password=password

Another thing I would consider is locking down the desktops so that users cannot change certain things. You can use sabayon for gnome to do this if you run Gnome. In KDE you can use KDE kiosk. 

[http://projects.gnome.org/sabayon/](http://projects.gnome.org/sabayon/)

Please let us know how the migration goes.

---

### Post by amadeus266 on 2009-05-20
Thanks kimda, I'll give it a go.

---

### Post by amadeus266 on 2009-05-21
Well, AD my be a no go... I think something is wrong with the DNS server configuration. My WinXP Pro computers join AD by looking for server.domain.local and Ubuntu can't seem to find it, but it can find server.domain.com but the IP address in not an internal address. I've tried several different how to's and other documentation so it must be something with the DNS server. I can still seamlessly run the applications we need though so that is a good start and my network printers work as well. Still moving forward...

---

### Post by kimda on 2009-05-22
Add the ip address of your windows dns server to the list in /etc/resolv.conf, like this:
nameserver 10.10.10.10  

or change these settings with the networkmanager. It should be able to ping the local domain.

---

### Post by amadeus266 on 2009-05-22
> **kimda said:**
> Add the ip address of your windows dns server to the list in /etc/resolv.conf, like this:
nameserver 10.10.10.10  

or change these settings with the networkmanager. It should be able to ping the local domain.

My resolv.conf contains the following:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.2.100
```
the 192.168..... is my Domain Controller with DNS server running

If I ping servername.domainname.local I get unknown host server.domainname.local.

Edit: If I try the same ping command on one of the windows machines, it works.

If I ping servername.domainname.com I get a response originating from opendns.

Is this correct? Or is there something wrong with the configuration of the DNS server on the win2k3 machine?

---

### Post by amadeus266 on 2009-05-22
Update: I have successfully joined the domain on the machine in question. I had to edit the nsswitch.conf as follows

```
hosts: files dns wins ...
```

I'm attempting to use Likewise-open. So far, it looks like it will do what I need.

---

### Post by kimda on 2009-05-22
Put the local dns server at the top instead of the bottom of the list so that it will query your local dns first.

---

### Post by amadeus266 on 2009-05-26
That is exactly what I did. Now that I have a proof-of-concept, I can move forward with the other non-essential workstations. I now have every one of my domain users able to log in to the first machine under their own credentials from the win2k3 server. 

Anyone here ever use Likewise Enterprise version? It looks like it is exactly what I need to get my entire network up to PCI DSS compliance.

---

### Post by horned0wl on 2009-05-27
> **amadeus266 said:**
> Well, AD my be a no go... I think something is wrong with the DNS server configuration. My WinXP Pro computers join AD by looking for server.domain.local and Ubuntu can't seem to find it, but it can find server.domain.com but the IP address in not an internal address. I've tried several different how to's and other documentation so it must be something with the DNS server. I can still seamlessly run the applications we need though so that is a good start and my network printers work as well. Still moving forward...

Hm.  I just joined an Ubuntu machine to Active Directory today, using "Likewise-Open," and had no problems at all.  My biggest issue is going to be setting a common */home* folder ("default user") that everyone sees when they log into active directory on the Ubuntu machine.  Your thoughts?

---

### Post by amadeus266 on 2009-05-29
I did manage to get my machine to join. But I tried using 9.04 and I am having some networking problems so I am going back to 8.04 and try again.

---

### Post by amadeus266 on 2009-06-03
> **horned0wl said:**
> Hm.  I just joined an Ubuntu machine to Active Directory today, using "Likewise-Open," and had no problems at all.  My biggest issue is going to be setting a common */home* folder ("default user") that everyone sees when they log into active directory on the Ubuntu machine.  Your thoughts?

I am also trying to figure this one. I would really like to have a specific set of shortcuts for all users.

---

