---
title: "azureus problems"
date: 2005-12-13
forum: General Help
---

### Post by hdagelic on 2005-12-13
I am trying to get Azureus working with Ubuntu Breezy 5.10 but no luck. I googled a lot but i didn't find anything helpful. 

Here is what I get when I try to test ANY incoming port including port 80:

>     Testing port 6881 ... Unable to test: Invalid port given, or test service failed.
>     Another application may already be using this port.


I read the howto on this site which says that i have to install firestarter to enable the port (WHY??) but firestarter doesn't work (it says that my ethernet device is not ready although i'm connected with PPPoE - PPP over ethernet).

I also tried:

 iptables -I INPUT -p tcp --dport 6881 -j ACCEPT

I have an dsl connection with PPPoE and it's firewall is off. Aruresus works fine with Windows so it's not an provider's firewall problem.


If somebody knows something... please help.


Hrvoje

---

### Post by jvictor on 2005-12-13
Are u using DHCP ? If so have u enabled portforwarding for ur linux machines IP? U have to turn on port forwarding on ur ADSL router.

---

### Post by hdagelic on 2005-12-13
hmm... No. I don't know how :(  But i did search a little.

---

### Post by tonysathre on 2005-12-13
look at this:

[http://www.nirvani.net/docs/port_forwarding_with_linux_2.2.x_ipmasqadm_portfw.htm](http://www.nirvani.net/docs/port_forwarding_with_linux_2.2.x_ipmasqadm_portfw.htm)

also, what router are your using? make? model?

---

### Post by codejunkie on 2005-12-13
[quote=hdagelic]I am trying to get Azureus working with Ubuntu Breezy 5.10 but no luck. I googled a lot but i didn't find anything helpful. 

Here is what I get when I try to test ANY incoming port including port 80:

>     Testing port 6881 ... Unable to test: Invalid port given, or test service failed.
>     Another application may already be using this port.


I read the howto on this site which says that i have to install firestarter to enable the port (WHY??) but firestarter doesn't work (it says that my ethernet device is not ready although i'm connected with PPPoE - PPP over ethernet).

I also tried:

 iptables -I INPUT -p tcp --dport 6881 -j ACCEPT

I have an dsl connection with PPPoE and it's firewall is off. Aruresus works fine with Windows so it's not an provider's firewall problem.


If somebody knows something... please help.


Hrvoje[/quote] i don't know if this is what is affecting you, but i couldn't get Azureus to work and gij was the cause of it. breezy includes a version of java by default and Azureus dosen't seem to like and even if you've installed the sun java package it will still use the one included in breezy until you remove the gij packages, i removed the gij packages and it's working fine now. open a terminal and copy this into the termiinal and paste the output here ```
java -version
```

---

### Post by lysis on 2005-12-13
[QUOTE=jvictor]Are u using DHCP ? If so have u enabled portforwarding for ur linux machines IP? U have to turn on port forwarding on ur ADSL router.[/QUOTE]

Keep in mind he said that in WINDOWS it works fine . . .

linux my not do so hot with Universal PnP compared to windows. I would turn off the uPnP somewhere in azureus options (i know it's there, just not at home to tell you where) and setup your router manually to foward the port that you use over to your ip address.

if you need help doing that we would need to know make and model of the router AND we would need to know your ip address to your PC. do you use DHCP or did you statically set your IP on your PC? you should setup a static IP to properly configure port forwarding.

Azureus does  NOT  perform as well for me as it does in Windows, but i'm learning to deal with it.

---

### Post by hdagelic on 2005-12-13
Thank you - that's it! It is the Java problem. Thank you also, tonysathre.

I removed the "gij" package, but that didn't remove the java binary, so I deleted it manually and installed Sun's latest version... Azureus is also starting 3 times faster now!

root@medo2:~/skripte# java -version

BEFORE:

java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

AFTER:

root@medo2:/home/hrvoje/progs/jre1.5.0_06# java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode)

---

### Post by codejunkie on 2005-12-13
[QUOTE=hdagelic]Thank you - that's it! It is the Java problem. Thank you also, tonysathre.

I removed the "gij" package, but that didn't remove the java binary, so I deleted it manually and installed Sun's latest version... Azureus is also starting 3 times faster now!

root@medo2:~/skripte# java -version

BEFORE:

java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

AFTER:

root@medo2:/home/hrvoje/progs/jre1.5.0_06# java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode)[/QUOTE]
i thought that might have been it glad to help.

---

