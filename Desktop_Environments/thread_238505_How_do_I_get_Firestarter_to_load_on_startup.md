---
title: "How do I get Firestarter to load on startup?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Maelgwyn on 2006-08-17
Hey all,

I'd love to get Firestarter to load on startup, but it comes up with an error message saying that I must be root to start Firestarter...

Help please!

---

### Post by kb3hkg on 2006-08-17
Why do you need it to run? firestarter is a frontend to iptables the firewall is there just not the gui at start up. unless there is a reason you need to see it it's not worth the fuss.

---

### Post by Maelgwyn on 2006-08-17
oh. I didn't know that! :redface:

In that case, nevermind lol

---

### Post by Koori23 on 2006-08-17
To explain a little better.. Firestarter only defines a default ruleset within IPTables. If you'll notice when your system boots, you'll see "Starting IPTables" or "Starting Firestarter" or something similar to that. The fact that you have the icon running is somewhat pointless as Maelgwyn has pointed out.

---

### Post by n00buntu NJ on 2006-08-17
> **Koori23 said:**
> To explain a little better.. Firestarter only defines a default ruleset within IPTables. If you'll notice when your system boots, you'll see "Starting IPTables" or "Starting Firestarter" or something similar to that. The fact that you have the icon running is somewhat pointless as Maelgwyn has pointed out.

But if you did feel like having it load, as I do (since I'm always playing with it), you could add "gksu firestarter" to your Sessions > Startup Programs list.  

For me it opens when I boot and I just kill it to the tray.  

:cool:

---

### Post by bluntu on 2006-08-18
Some programs silently connects to the net on Windows and firewalls like ZoneAlarm/Segates detects it.

Can Firestarter detects outbound connections with an Alert Box with a choice "Allow" or "Deny"?

---

### Post by gannic on 2006-08-27
> **bluntu said:**
> Some programs silently connects to the net on Windows and firewalls like ZoneAlarm/Segates detects it.

Can Firestarter detects outbound connections with an Alert Box with a choice "Allow" or "Deny"?


Its a good point - is there any way to configure firestarter by program?

I like Ubuntu a lot, but it does concern me that many of the programs I download are created by enthusiasts. Out of the many, only one needs to contain something malicious....a key logger or something. From what I can see, as it stands the IPtables let anything through.

---

### Post by Anduu on 2006-08-28
> **gannic said:**
> Its a good point - is there any way to configure firestarter by program?

I like Ubuntu a lot, but it does concern me that many of the programs I download are created by enthusiasts. Out of the many, only one needs to contain something malicious....a key logger or something. From what I can see, as it stands the IPtables let anything through.

No you cant configure Firestarter by program.

Just like in Windows if you go installing programs from sources you don't know and trust you stand the chance of getting burned.

---

### Post by asplode on 2006-08-28
I wonder if keyloggers exist for linux.

---

### Post by Fraoch on 2006-08-28
Take a look at this from the Firestarter FAQ at [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

I'm trying to get this going with varying results.  Post to follow later, but I can get sudo firestarter to work without it asking me for a password.

---

### Post by Anduu on 2006-08-28
> **Fraoch said:**
> Take a look at this from the Firestarter FAQ at [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

I'm trying to get this going with varying results.  Post to follow later, but I can get sudo firestarter to work without it asking me for a password.

Before you go through all the trouble that method doesn't work in Dapper.

---

### Post by Fraoch on 2006-08-28
> **Anduu said:**
> Before you go through all the trouble that method doesn't work in Dapper.

OK - what does?

---

### Post by Anduu on 2006-08-28
I remember from a while back(2 or 3 months...) there was a hack/workaround which involved monkeying with the sudoers file(not the one linked to in this thread...) which I personally wasn't comfortable doing(meaning I didn't trust the methods used to not break something serious down the road...)

The thread is still on the forums somewhere...you'll just have to do some digging...

---

### Post by Fraoch on 2006-08-28
I'll do a search and make a separate post if necessary.  Thanks.

---

### Post by rjg1021 on 2006-08-31
> **n00buntu NJ said:**
> But if you did feel like having it load, as I do (since I'm always playing with it), you could add "gksu firestarter" to your Sessions > Startup Programs list.  

For me it opens when I boot and I just kill it to the tray.  

:cool:

Hey, thanks for that tip. One thing though, I am asked for my password at start-up. 

I tried the /etc/sudoers edit from the [firestarter FAQ ]("http://www.fs-security.com/docs/faq.php#trayicon"):

```
username ALL= NOPASSWD: /usr/bin/firestarter
```

It "broke" the command so that the firestarter front-end would no longer load on start-up. Anyone have a fix to make firestarter load on start-up w/O it prompting for root password?

---

### Post by bluntu on 2006-09-18
> **gannic said:**
> Its a good point - is there any way to configure firestarter by program?

I like Ubuntu a lot, but it does concern me that many of the programs I download are created by enthusiasts. Out of the many, only one needs to contain something malicious....a key logger or something. From what I can see, as it stands the IPtables let anything through.

Well I found a simple solution (might not be the best). Whenever I'm feeling paranoid about a program making outbound connection I turn on Ethereal (root) before I run the program.

Picasa on Windows connects to the net. On Linux it doesn't, according to Ethereal.

---

### Post by fabertawe on 2006-09-18
> **Koori23 said:**
> To explain a little better.. Firestarter only defines a default ruleset within IPTables. If you'll notice when your system boots, you'll see "Starting IPTables" or "Starting Firestarter" or something similar to that. The fact that you have the icon running is somewhat pointless as Maelgwyn has pointed out.

Apologies if this sounds obvious to everyone bar me... so if I define some inbound policies with Firestarter's GUI, then those policies are now permanently active irrespective of whether or not I continue to run Firestarter?

Cheers ... Paul

---

### Post by _asc_ on 2006-09-18
Yes, because netfilter/iptables is the firewall and firestarter is just a visual configuration editor for iptables:

[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)

---

### Post by fabertawe on 2006-09-18
> **_asc_ said:**
> Yes, because netfilter/iptables is the firewall and firestarter is just a visual configuration editor for iptables:

[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)

Ahhh, thankyou very much for that. A new user (such as myself :wink:) might not have realised this! I'd best check exactly what rules I have set...

Cheers ... Paul

---

### Post by Roobert on 2006-09-26
So if I installed firestarter through Synaptic, and configured it with the wizard, my settings will always be honored upon startup?

~Roobert.

---

### Post by arjaybe on 2006-09-26
> **Roobert said:**
> So if I installed firestarter through Synaptic, and configured it with the wizard, my settings will always be honored upon startup?

~Roobert.

Yes.

---

### Post by compwiz18 on 2006-10-28
Really? Because my port scanner tells me differently...

---

### Post by girard on 2007-03-27
> **_asc_ said:**
> Yes, because netfilter/iptables is the firewall and firestarter is just a visual configuration editor for iptables:

[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)

excuse me...

Meaning the firewall (firestarter) was there even before the GUI was installed? and its always turned on?

---

### Post by compwiz18 on 2007-03-27
On a clean Ubuntu install, the machine is safer then XP with a firewall.  However, if you run around installing various servers like me, you should install Firestarter.  If you haven't installed anything servers, then you should be safe.

---

### Post by compwiz18 on 2007-03-30
> Version 6.10 was released in October 2006 as a single CDROM image.92 Ubuntu utilizes the LiveCD notion for an environment and enables the network device immediately, even before the installation GUI appears. However, a preliminary Nmap scan against this configuration reveals there are no remotely accessible network services available on the machine. The Ubuntu installer only responds to an ICMP ping. Additionally, the TCP/IP stack did not reveal its fingerprint for system identification. Even after rebooting the system, Ubuntu's Edgy desktop edition did not present any remote entry points into the system. A quick check with netstat -l revealed that all socket activity on the system was limited to localhost UNIX streams. A quick Nmap scan identified the Ubuntu system as having no open ports and could only fingerprint the system as Linux 2.6. Nessus was unable to identify any vulnerable risks to the host in the default configurations.

from [http://www.omninerd.com/2007/03/26/articles/74](http://www.omninerd.com/2007/03/26/articles/74)

---

