---
title: "Failed to check for installed and available applications"
date: 2009-09-29
forum: Desktop Environments
---

### Post by kaolakeya on 2009-09-29
(11:17:35 AM) kaolakeya: I am trying yo use the Add/Remove programs tool in Ubuntu 9.04, Jaunty edition, but get the following error message: 
(11:17:35 AM) kaolakeya: Failed to check for installed and available applications
(11:17:35 AM) kaolakeya: This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
(11:17:35 AM) kaolakeya: ------------------------------------------------------------------------------------------------
(11:17:35 AM) kaolakeya: I have tried the commands, but without success. then I renamed the /etc/apt/sources.list to sources.list.org, removed the sources.list and tried again, but it didn't help. so i copied sources.list.org to sources.list. i have also tried the main server and from united states (default was from sweden), but no success. error message in the command prompt when trying update and upgrade commands:
(11:17:35 AM) kaolakeya: Get:36 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) intrepid-updates/multiverse Sources [4678B]
(11:17:35 AM) kaolakeya: Fetched 9727kB in 27s (352kB/s)                                                
(11:17:35 AM) kaolakeya: Reading package lists... Error!
(11:17:35 AM) kaolakeya: E: Encountered a section with no Package: header
(11:17:35 AM) kaolakeya: E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
(11:17:35 AM) kaolakeya: E: The package lists or status file could not be parsed or opened.
(11:17:35 AM) kaolakeya: ------------------------------------------------------------------------------------------------
(11:17:35 AM) kaolakeya: Please help!

---

### Post by jerrrys on 2009-09-29
(11:17:35 AM) kaolakeya: Get:36 [http://ph.archive.ubuntu.com]("http://ph.archive.ubuntu.com/") intrepid-updates/multiverse Sources [4678B]

this is a source for interpid (8.10) and your running jaunty (9.04).  don't think this is going to work

---

### Post by kaolakeya on 2009-09-29
Hello and thanks for the fast reply!
I have copied several different versions of the sources.list in a desperate attempt to fix the problem, but nothing seems to solve it. Could anyone please provide me with the content of a working sources.list for ubuntu 9.04 jaunty edition?

---

### Post by jerrrys on 2009-09-29
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

this is the basic sources that you need

[ATTACH]130177[/ATTACH]

---

### Post by kaolakeya on 2009-09-30
Hello again, thanks for that great site! However, updating the sources.list does not do the trick i'm afraid. First I chose widely, not ok. Then i chose just the main apps, same error. I ran the recommended commands (below) with the following error message:

kaolakeya@kaolakeya-laptop:/etc/apt$ sudo apt-get update
Get:1 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) jaunty Release.gpg
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) jaunty/main Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US    
Get:2 [http://deb.opera.com](http://deb.opera.com) stable Release [1067B]                    
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) jaunty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Ign [http://deb.opera.com](http://deb.opera.com) stable Release        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                   
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                   
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) jaunty/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) jaunty/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Fetched 190B in 0s (708B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
kaolakeya@kaolakeya-laptop:/etc/apt$ sudo apt-get install -f
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
kaolakeya@kaolakeya-laptop:/etc/apt$ 
----------------------------------------

So, maybe some other list that causes the problem? I think this started after installing Opera, but I am not sure...
Any suggestion?

---

### Post by jerrrys on 2009-09-30
forget this; be back

---

### Post by kaolakeya on 2009-10-01
I'm sorry, I don't understand what you mean. Will you be back later?

---

