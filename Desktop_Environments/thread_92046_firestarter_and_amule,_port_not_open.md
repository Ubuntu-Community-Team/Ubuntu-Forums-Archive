---
title: "firestarter and amule, port not open"
date: 2005-11-18
forum: Desktop Environments
---

### Post by korami on 2005-11-18
Hi everybody. 

I downloaded aMule from the repos, connected successfully and started a download, which is now in progress. I'm using firestarter as firewall, and though I didn't get to open for inbound trafic the port that aMule uses (4662 seems to be default), I observed in aMule's *Transfers* window that there are active uploads for the file I'm downloading.

Now I don't have any issue with people downloading from me via aMule (that's the whole concept of sharing), I'm still wondering how that can happen with the port not yet open for inbound? Does firestarter not protect me as it should?

Or am I missing something here, like maybe the fact that there is no inbound traffic actually, because my aMule client "offered" to upload the file to anyone that requests it? 

I don't have knowledge about how these P2P apps work, so sorry if the answer is obvious.

---

### Post by dragonfoundry on 2005-11-18
[QUOTE=korami]
I downloaded aMule from the repos, connected successfully and started a download, which is now in progress. I'm using firestarter as firewall, and though I didn't get to open for inbound trafic the port that aMule uses (4662 seems to be default), [/quote]

I had to configure Firestarter to open up the emule ports as I was getting a Low ID (which sucks). 

To make sure you havent got a Low ID, which will affects your ability to get the files you want go to 
[Amule Test Port]("http://www.amule.org/testport.php"). If it reports a success your okay, if not you will need to configure firestarter to get the most out of amule. 

Theres a good page on emule about High ID and Low ID called [ID explained]("http://www.emule-project.net/home/perl/help.cgi?l=1&rm=show_topic&topic_id=103")

---

### Post by korami on 2005-11-18
Thanks dragonfoundry, this helped indeed to speed up my downloads.

I was wondering about something else though (maybe I wasn't verry clear), that is how come people can download from me through aMule though I had the port 4662 not opened for **inbound** trafic at that time, which means that connections originating from the internet should have not been allowed by the firwall.

But as I said earlier, I'm probably missing something here.

---

### Post by Icefox on 2005-11-18
Hi,i also use firestarter and aMule-but don't have this problem...so try to allow this port from firewall.

---

### Post by dragonfoundry on 2005-11-19
[QUOTE=korami]
I was wondering about something else though (maybe I wasn't verry clear), that is how come people can download from me through aMule though I had the port 4662 not opened for **inbound** trafic at that time, which means that connections originating from the internet should have not been allowed by the firwall.

But as I said earlier, I'm probably missing something here.[/QUOTE]


If port 4662 is not open then your IP cannot be determined however, it doesnt mean uploading and downloading is not possible.

What happens is that the server your connected to assigns a Low ID and all requests (connection, queue requests) to your computer are routed over the server to which you are connected.

Thus data can be sent and received. However, this puts strain on the server you are connected to and sometimes serves restrict the number of Low ID users or drop them if the load becomes too much. Some servers will not let you connect with a Low ID.

Also two users with Low IDs cannot connect to each other as it is not possible to route over two different servers. 

If a server becomes to busy there is also a risk that queue position and requests as well as messages get lost.

So you can see even though you can use amule without having port 4662 open having traffic routed over the server your connected to isnt really ideal.

Hope that helps.

---

### Post by korami on 2005-11-20
[QUOTE=dragonfoundry]If port 4662 is not open then your IP cannot be determined however, it doesnt mean uploading and downloading is not possible.

What happens is that the server your connected to assigns a Low ID and all requests (connection, queue requests) to your computer are routed over the server to which you are connected.
[/QUOTE]

Ok, now it is clear. I thought that because the port 4662 is not open, no uploading should be allowed by firestarter. But I see now that the upload is initiated by me, which should be allowed by the firewall.

Thanks for your help dragonfoundry.

---

### Post by robertobech on 2005-12-17
My experience: I tried to open the 4662 port on firestarter, on the "allow service" section. However, seems like I was allowing the right port on the wrong section: what really worked was to allow port 4662 on the section "forward service". I don't know if this is obvious to you all here, but anyway, here it goes for the beginners like me - and please tell me  if I am doing something wrong, ok?

**AMULE - Low ID?**
If you're having problems with "Low ID" on amule, try this link:
[http://www.amule.org/testport.php](http://www.amule.org/testport.php)
(you should have amule opened before visiting the site, or else the test won't work)

Click on "Test". It will test the 4662 port on your sytem. If it's not open, you'll receive some kind of error message.

If this is the case, install firestarter, and then open the "policy" tab. Click on the "forward service" section, then "Add rule". Then: 

name: eDonkey
Port: 4662
IP or HOST: (your IP, such as 192.168.0.1)
Port: 4662

---

### Post by utab on 2006-02-02
If this is the case, install firestarter, and then open the "policy" tab. Click on the "forward service" section, then "Add rule". Then:

name: eDonkey
Port: 4662
IP or HOST: (your IP, such as 192.168.0.1)
Port: 4662

The forward section is not accessible, what to do?

---

### Post by deBaas on 2006-02-02
[QUOTE=utab]If this is the case, install firestarter, and then open the "policy" tab. Click on the "forward service" section, then "Add rule". Then:
name: eDonkey
Port: 4662
IP or HOST: (your IP, such as 192.168.0.1)
Port: 4662
The forward section is not accessible, what to do?[/QUOTE]
Please don't. You won't have to use the forward section. It's only availibe if you have more that one NIC. And you would only use it if amule was running on the PC connected to the second NIC.

---

