---
title: "Oracle 10g/11g &amp; Saybase12.5/15.*"
date: 2011-06-14
forum: Desktop Environments
---

### Post by freewdiny on 2011-06-14
I'd like to know anyone ever installed Oracle 10g/11g and Sybase 12.5/15.* successfully in Desktop Ubuntu 10.10 or 11.04.
I tried several time, but can not successfully.
I just changed to use ubuntu 3 months agao. 
If Oracle & Sybase can not installed successfully, I must give up to use ubuntu.

Thanks

---

### Post by bencouve on 2012-06-24
I am looking at this myself now so will let you know how I get on.

---

### Post by bencouve on 2012-06-25
Just so you know - this is in progress .... Please take a look at this web site.

[https://forums.oracle.com/forums/thread.jspa?threadID=2301639&tstart=0](https://forums.oracle.com/forums/thread.jspa?threadID=2301639&tstart=0)

I have worked through to chapter 7. Have used internal hard drive for the configuration. So far all commands have executed successfully. If you follow the instructions I suggest you use a copy Gparted from CD and not USB. I got an error with the USB and the CD works ok, so far so good anyway. About to start Oracle install...

Will keep you posted.

---

### Post by bencouve on 2012-06-25
It would appear Oracle is installed, mounted and running, but with a few errors.

First off, I am no Oracle expert but this may help someone. I am sure the experts will be
able to blow holes in this at every turn. I used the link previously posted but get errors after the 

sudo /etc/init.d/oracle-xe configure

In chapter 8

To resolve this I tried entering

mount -t tmpfs shmfs -o size=2048m /dev/shm

into file "/etc/init.d/oracle-shm"

as instructed in this url

[https://cn.forums.oracle.com/forums/thread.jspa?threadID=2376116](https://cn.forums.oracle.com/forums/thread.jspa?threadID=2376116)

However, that did not work either. So I tried creating a partition using
Gparted. This is also suggested in the above url. Here it is

shmfs            2097152   624088   1473064  30% /dev/shm

Note: so far have left the entry

mount -t tmpfs shmfs -o size=2048m /dev/shm

in /etc/init.d/oracle-shm

but may remove it later

This appears to have worked. I still got errors when running 
sudo /etc/init.d/oracle-xe configure but I can start the db. Will continue with this tomorrow as it is late.
One other thing, the url for apex or xe, does not work yet, this one

[http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex)

You may find this useful too. 

[http://mediakey.dk/~cc/howto-install-oracle-on-debian/]("http://mediakey.dk/%7Ecc/howto-install-oracle-on-debian/")

---

### Post by bencouve on 2012-06-27
This will be my last post to this question. Think this has been aced. The final URL that any views may find useful is

[https://forums.oracle.com/forums/thread.jspa?messageID=10127977&#10127977](https://forums.oracle.com/forums/thread.jspa?messageID=10127977&#10127977)

I had difficulty getting the XE application to connect at 

[http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex)

However, the problem was that as I had installed oracle a few times the port in the listener.ora file was set to 1521 as it was in tnsnames.ora , but after running this command from SQL>

show parameter listener

I found that oracle was set for 1530. This is because I had entered 1530
during the installs after the first install as 1521 had been taken
after the first install.

Once I aligned listener.ora dn tnsnames.ora with the db I was able to see
the xe interface.

---

### Post by bencouve on 2012-07-06
Ok, so I lied, here is another post.

The errors that are mentioned above may be a permissions thing. I had noticed that some of the . and .. file/folders, what ever they are, had root root permissions. So what I did was recursively change all permissions to oracle dba. I have a post for this recursive change but did not specify in that post that it is for oracle dba permissions. So do this

chown -hR oracle:dba /u01/app

My Oracle Apex appears to be working ok now. I am about to import an application I developed about a year ago with apex so will be interesting to see how that goes. 

Anyone reading this, all the best with your Apex install on Ubuntu. It took me a lot of time and determination to get this installed. Probably because I am very rusty when it comes to Unix/Linux, but hey, I did it...

---

### Post by katanacb on 2012-07-06
Don't know if you are still interested in the Sybase question, or what version of Ubuntu you are wanting to know of, but yes, you can easily install Sybase ASE inside of Ubuntu.

the 12.5.x series is EOL ... the latest 12.5.4 ESD *SHOULD* work inside of 10.04; I had it running there.

15.x runs inside of 10.04 LTS, 10.10 ... I have not tried 12.04.   Let me know if you are interested and I'll try it in my VM.

Of course Sybase doesn't officially support ASE on Ubuntu, but that doesn't mean it won't run.

HTH...

---

### Post by wildmanne39 on 2012-07-06
Hi, this is an old thread that was not answered within a year so it as been closed, thanks for sharing your solution and if you need help please start a new thread.

---

