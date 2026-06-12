---
title: "LDAP PDC with SAMBA shares for WinXP-SP2"
date: 2009-10-04
forum: Desktop Environments
---

### Post by UbuntooTheBestLinux on 2009-10-04
Hello everyone,

This my first post to the UBUNTU forums.  I'm fairly new to linux.  I'm trying to get an LDAP PDC with SAMBA running inside of VMWARE workstation 6.5.  I have followed all the steps in the [OpenLDAP-SambaPDC-OrgInfo-Posix]("https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix?action=fullsearch&context=180&value=linkto%3A%22OpenLDAP-SambaPDC-OrgInfo-Posix%22") documentation, located at [https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix](https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix).  

I can see the LDAP Server in Nautilus on a Fedora host on the same network, as well as from my Windows XP host on the network.

When I try to access the shares on my LDAP/SAMBA server from Fedora, I get an error message:  Unable to mount location ( Failed to retrieve share list from server ).

When I try to access the shares on the LDAP/SAMBA server from Windows XP client, through the 'Network Places' section, I get a login prompt that says "Connecting to Linuxpc".  Linuxpc is the workgroup name of my LDAP/SAMBA server.  When I enter the username and password nothing happens.  When I try to access the domain 'server', the domain of my LDAP/SAMBA server, I get the error message:  Logon failure:  unknown user name of bad password.

Running nmap from Fedora client shows that ports 139, 389, and 445 are open on the LDAP/SAMBA server.

Any help will be greatly appreciated.  

Thank you...

---

### Post by lirel on 2009-10-04
IMHO you should ask this question in the general-help or networking section again, because this sounds more like a samba-related problem.

---

