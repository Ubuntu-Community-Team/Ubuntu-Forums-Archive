---
title: "could not obtain ip..."
date: 2005-09-12
forum: Desktop Environments
---

### Post by MrJangles on 2005-09-12
I'm quite new to ubuntu so bare with me... 

I'm using 5.04 with kde, and i'm getting a "could not obtain ip address" from wifi-radar when i try to a wireless network. I've never had this problem. Connecting to wireless networks has always worked for me in ubuntu using wifi-radar. And just today it gives me this error message when i'm trying to connect. the signal is strong, its sending and recieving, but it cant get an ip. its dhcp. 

I've tried reseting everything, deleted my settings, and starting over. I still get the same error. any ideas? i also dont like wifi-radar, is there an alternative application to configure my wireless networks without using command-line?

Thanks

---

### Post by mlomker on 2005-09-12
Kubuntu comes with kwifimanager, but it's nothing special.  

I haven't used wifiradar before.  Some diagnostic commands that might help:

[b]
iwconfig
ifconfig
dmesg | more
[/b]

Does iwconfig showing that you are attached to the access point?  Does it have security (WEP)?

---

### Post by MrJangles on 2005-09-12
hmm.. wifi-radar is saying i'm connected to the wireless network, but it cant obtain the ip. its not encrypted, its an open connection. "Connected to (network) ip(None). then i connect, wifi-radar "acquiring ip address" hangs there for a bit than gives the could not get ip add error. I dont know what to do with those commands you posted. :(

---

### Post by MrJangles on 2005-09-12
what is the default sources.list ? is it possible to post that ? :)

---

### Post by mlomker on 2005-09-13
[QUOTE=MrJangles]what is the default sources.list ? is it possible to post that ? :)[/QUOTE]

This isn't the default, but it includes everything;

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-backports main restricted universe multiverse

---

### Post by mlomker on 2005-09-13
[QUOTE=MrJangles]I dont know what to do with those commands you posted. :([/QUOTE]

Type them in at a terminal prompt.  Most of us linux-weenies do things from the command prompt.   :razz:

---

### Post by aveline on 2005-09-13
[QUOTE=mlomker]Type them in at a terminal prompt.  Most of us linux-weenies do things from the command prompt.   :razz:[/QUOTE]
 find the unofficial ubuntu guide on the web (don't have the addy to hand)... it will help you add sources quickly.

if you want a more gui way to do it, the wiki has an example too but i found the guide simpler.

aveline

---

