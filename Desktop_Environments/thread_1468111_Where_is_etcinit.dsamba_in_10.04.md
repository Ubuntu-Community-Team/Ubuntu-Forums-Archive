---
title: "Where is /etc/init.d/samba in 10.04?"
date: 2010-05-01
forum: Desktop Environments
---

### Post by thebrotherofasis on 2010-05-01
In the old days (9.10) samba service used to be located in /etc/init.d/samba

Where did it go in 10.04?

I installed samba using

```
sudo apt-get install samba smbfs
```

and restarted the computer.

Now, doing 

```
findsmb
```

works ok.

However, if I want to restart the service after editing smb.conf by running

```
sudo /etc/init.d/samba restart
```

it outputs

> sudo: /etc/init.d/samba: command not found

Then I open a terminal and navigate to /etc/init.d/ and I can't see samba there.

However, samba is working ok and identifying all computers in my home network.

Where did the service go then?

Thank you!

---

### Post by Morbius1 on 2010-05-01
Two things have happened - "upstart" has replaced the old way of starting services and the "samba" service has been replaced by the old way of separating the smbd and nmbd daemons.

So the way you need to restart samba is now this way:

sudo service smbd restart
sudo service nmbd restart

---

### Post by thebrotherofasis on 2010-05-01
Thank you.

It shows then now.

---

### Post by pupEOkami on 2010-06-05
> **Morbius1 said:**
> Two things have happened - "upstart" has replaced the old way of starting services and the "samba" service has been replaced by the old way of separating the smbd and nmbd daemons.

So the way you need to restart samba is now this way:

sudo service smbd restart
sudo service nmbd restart


now will they make a fix or patch for webmin
Access control violation : /etc/init.d/samba start failed

---

### Post by Morbius1 on 2010-06-05
> **pupEOkami said:**
> now will they make a fix or patch for webmin
Access control violation : /etc/init.d/samba start failed
According to this it's in the next release of webmin:
[http://sourceforge.net/tracker/index.php?func=detail&aid=2995073&group_id=17457&atid=117457](http://sourceforge.net/tracker/index.php?func=detail&aid=2995073&group_id=17457&atid=117457)

You know when I originally posted this:
> Two things have happened - "upstart" has replaced the old way of  starting services and the "samba" service has been replaced by the old  way of separating the smbd and nmbd daemons.

So the way you need to restart samba is now this way:

sudo service smbd restart
sudo service nmbd restart     I was unaware that there was a third change to all of this - just to aggravate and confuse those of us not on the "need to know" mailing list:

Back in the good old days ( 6 months to a year ago ) if smbd was stopped or not started and you did a "sudo service smbd restart" it would start the daemon. Not any longer:
> sudo service smbd stop
   [COLOR=Blue]smbd stop/waiting[/COLOR]
sudo service smbd restart
   [COLOR=Blue]restart: Unknown instance:[/COLOR] The only logic I can think of for this change is that it is now grammatically correct - you can't restart something that hasn't started :roll:  So if smbd is stopped you need to do a "sudo service smbd start"

---

### Post by gabak on 2010-06-21
why did they do that? why confuse ppl?
is there any reasonable explanation?

---

### Post by Jml79 on 2010-07-30
Somebody needs to update the docs. The 10.04 server guide still has "/etc/init.d/samba restart" in its documentation for samba. Very confusing.

also, "restart smbd" works. This is all that I have needed after a change to the smb.conf file.

edit: already reported to docs bug teacker. Hopefully it will get updated soon.

---

### Post by gabak on 2010-08-02
how can i report that bug without hassle?

---

### Post by matthewdial on 2010-08-10
Ubuntu 10.04 server ed.
Samba 3.4.7

> **Morbius1 said:**
> Two things have happened - "upstart" has replaced the old way of starting services and the "samba" service has been replaced by the old way of separating the smbd and nmbd daemons.

So the way you need to restart samba is now this way:

sudo service smbd restart
sudo service nmbd restart

When I try the smbd restart I receive "restart: Unknown instance:"

I'm new to this and not sure what in the world I'm doing (including did I post in the wrong place since this thread is labeled "Solved"?). I've tried configuring it via CLI and also Webmin. But as mentioned above, restarting Samba in Webmin does not work.

---

### Post by Morbius1 on 2010-08-11
> **matthewdial said:**
> Ubuntu 10.04 server ed.
Samba 3.4.7
When I try the smbd restart I receive "restart: Unknown instance:"

You didn't read the rest of my posts.

If smbd is already running and you want to restart samba:
```
sudo service smbd restart
```If smbd is currently not running:
```
sudo service smbd start
```If you use "restart" when smbd in not running you will get the error message:
> "restart: Unknown instance:"All of this is not as it used to be. Before you could use "restart" to start a service that is not running. They must have hired a developer that is very persnickety about grammar - you can't restart something that hasn't started ;)

---

### Post by chaumurky on 2010-08-15
> **Morbius1 said:**
> ...They must have hired a developer that is very persnickety about grammar - you can't restart something that hasn't started ;)

But what if it had started and then stopped? Wouldn't I restart it? :P

---

### Post by herauthon on 2010-08-22
:KS
Checked the boot and startup processes in webmin
viewed content of the mechanics.

found:  service
Usage: service < option > | --status-all | [ service_name [ command | --full-restart ] ]


service smbd start 
smbd start/running, process 1510

service nmbd start
nmbd start/running, process 1527

made 2 shell scripts

open shell and..

cd /etc/init.d
echo service smbd start > samba-up
echo service nmbd start >> samba-up

echo service smbd stop > samba-down
echo service nmbd stop >> samba-down

chmod +rx samba-up samba-down

replace the Samba start/stop entries in Webmin
with /etc/init.d/samba-up - and /etc/init.d/samba-down


issue resolved?

---

### Post by andydread on 2010-08-25
So now How does one disable the starting of samba on boot?   Back about a decade ago when I setup Red Hat and Mandrake servers it was as simple as 
```
service smb off
``` 

I used to be able to apt-get install rcconf and disable it there.  does rcconf play well with upstart? 

How does one simply disable samba on boot now that everything is moved to upstart.

---

### Post by doubleu- on 2010-08-27
lol the documentation needs changed too

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html")

> #

Finally, restart the samba services to enable the new configuration:

sudo /etc/init.d/samba restart


---

### Post by dremelts on 2010-09-13
> **Morbius1 said:**
> Two things have happened - "upstart" has replaced the old way of starting services and the "samba" service has been replaced by the old way of separating the smbd and nmbd daemons.

So the way you need to restart samba is now this way:

sudo service smbd restart
sudo service nmbd restart

Does this detach the daemons so they run in the background?  Just today I set up samba and after making changes to the smb.conf file I used the above commands to restart samba.  All was good until I logged out of the server and people lost their connections to the network share.  So I restarted them again and left the server logged in until I could sort it out.

---

### Post by hagfish52 on 2012-01-29
It looks like you should have to use initctl to start or stop SAMBA, but there is some problem with the /etc/init/smbd.conf file used by Upstart that prevents it from working.  Anybody have any ideas about how to modify the script so it will work correctly? --John

---

