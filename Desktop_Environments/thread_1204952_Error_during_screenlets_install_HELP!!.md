---
title: "Error during screenlets install HELP!!"
date: 2009-07-05
forum: Desktop Environments
---

### Post by Blacklightbulb on 2009-07-05
I'm trying to install screenlets:
```

sudo apt-get install screenlets
```

and the following error occures:

```
Setting up nullmailer (1:1.04-1.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing nullmailer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nullmailer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It's something with the repos? Help!!

---

### Post by Blacklightbulb on 2009-07-05
Also this might help:

```
xxxx@xxxx-desktop:~$ sudo dpkg --configure -a
[sudo] password for xxxx: 
Setting up nullmailer (1:1.04-1.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing nullmailer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nullmailer
xxxx@xxxx-desktop:~$ 

```

---

### Post by Blacklightbulb on 2009-07-05
OK Resolved :lolflag: 

now... how do you close a thread?

if it's still open reply!:lolflag:

---

### Post by chrisinpants on 2012-12-04
Thread tools > Mark as solved

and of course tell us how you solved it ;)

EDIT: 3 1/2 years ago

---

### Post by wildmanne39 on 2012-12-04
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

