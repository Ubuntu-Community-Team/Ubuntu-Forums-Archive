---
title: "Lan Network Hw?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Branta on 2006-08-17
Ubuntu 6.06 LTS - the Dapper Drake

**_What do I do to set up a network between 2 Ubuntu computers_**?  

(Internet works with dhcp right from install).

--- Bob ---

---

### Post by gerbman on 2006-08-17
> **Branta said:**
> Ubuntu 6.06 LTS - the Dapper Drake

**_What do I do to set up a network between 2 Ubuntu computers_**?  

(Internet works with dhcp right from install).

--- Bob ---The easiest way is to plug your cable modem into a router and connect the two Ubuntu machines to the router. If this much is already in place, then it depends on what you want to do with your network. If you just need ssh/sftp, then installing the 'ssh' package should be sufficient. You can set up file sharing with Samba. Is there something else you wanted to do?

---

### Post by Branta on 2006-08-18
I want to transfer files between the Host and Client computers.  I want the Client computer to see and use the printers connected to the Host computer.

--- Bob ---

---

### Post by gerbman on 2006-08-18
> **Branta said:**
> I want to transfer files between the Host and Client computers.  I want the Client computer to see and use the printers connected to the Host computer.

--- Bob ---You can do that with Samba. [This]("http://ubuntuforums.org/showpost.php?p=1265314&postcount=2") is one way to set up Samba as a file server. I've not set up a print server before, but you'll be editing the same /etc/samba/smb.conf file to do it. Search for "samba print server" and the like within this forum and Google...there should be plenty of information out there.

---

