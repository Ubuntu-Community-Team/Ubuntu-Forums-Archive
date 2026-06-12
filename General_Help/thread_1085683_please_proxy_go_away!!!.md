---
title: "please proxy go away!!!"
date: 2009-03-03
forum: General Help
---

### Post by houcem on 2009-03-03
Hi everygeek, can you tell me why even when all proxy settings are removed I always get this when I install a package:

houcem@houcem-hpc6820s:~$ sudo apt-get install links
[sudo] password for houcem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  links
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 492kB of archives.
After this operation, 1147kB of additional disk space will be used.
Get:1 [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) intrepid/universe links 2.1pre37-1.1 [492kB]
Fetched 492kB in 39s (12.5kB/s)                                                
Selecting previously deselected package links.
(Reading database ... 181416 files and directories currently installed.)
Unpacking links (from .../links_2.1pre37-1.1_i386.deb) ...
Processing triggers for man-db ...
[[B][I][B][U][SIZE="2"]B]Setting up msttcorefonts (2.5) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
Error parsing proxy URL [http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:](http://bchaabane.houssemeddine@etudiant.turen.tn:250986@192.168.0.1:8080/:) Bad port number.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1[/B][/SIZE][/U][/B][/I][/B]
Setting up links (2.1pre37-1.1) ...

Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

it looks like apt-get tries to install a package:"msttcorefonts (2.5)" but the proxy configuration that I can' get rid of prevents the action from completing do you have any idea how to solve the problem?

---

### Post by NoReflex on 2009-03-03
Hello!

First make sure that there are no proxy settings in System -> Preferences -> Network Proxy.
You can also check Synaptic for any proxy settings and clear them out.
You should check the file /etc/apt/apt.conf and remove any proxy settings like : 
```
Acquire::http::Proxy "http://DOMAIN\NAME:PWD@PROXY.COM:PORT"
```

You could also try using wget to see if you can download some files.

Best wishes
NoReflex

---

### Post by houcem on 2009-03-05
Thanks a lot for your response. As I said I've cleared proxy settings everywhere:Network, Synaptic and even apt.conf( aquire::http::proxy "disable" also tried "direct" ) but always the same problem!

---

### Post by NoReflex on 2009-03-05
Can you try and download a .deb file from the Ubuntu repository using wget and then install it with dpkg?
For example tilda - which I use al, the time :
wget [http://za.archive.ubuntu.com/ubuntu/pool/universe/t/tilda/tilda_0.09.6-1_amd64.deb](http://za.archive.ubuntu.com/ubuntu/pool/universe/t/tilda/tilda_0.09.6-1_amd64.deb)

Best wishes,
NoReflex

---

### Post by Slim Odds on 2009-03-05
> **NoReflex said:**
> For example tilda - which I use al, the time :
wget [http://za.archive.ubuntu.com/ubuntu/pool/universe/t/tilda/tilda_0.09.6-1_amd64.deb](http://za.archive.ubuntu.com/ubuntu/pool/universe/t/tilda/tilda_0.09.6-1_amd64.deb)


Or... the 32 bit version..... depending on which Ubuntu you use.

---

### Post by houcem on 2009-03-07
Yes I can do that.

---

### Post by waffen on 2009-03-25
> **NoReflex said:**
> Hello!

First make sure that there are no proxy settings in System -> Preferences -> Network Proxy.
You can also check Synaptic for any proxy settings and clear them out.
You should check the file /etc/apt/apt.conf and remove any proxy settings like : 
```
Acquire::http::Proxy "http://DOMAIN\NAME:PWD@PROXY.COM:PORT"
```

You could also try using wget to see if you can download some files.

Best wishes
NoReflex

I can't! :confused: any idea???

---

