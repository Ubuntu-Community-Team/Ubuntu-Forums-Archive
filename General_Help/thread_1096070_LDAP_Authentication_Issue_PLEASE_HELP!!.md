---
title: "LDAP Authentication Issue PLEASE HELP!!"
date: 2009-03-14
forum: General Help
---

### Post by tomwoollard on 2009-03-14
I was wondering if someone could help me with the below Linux\LDAP issue

I am relatively new to Linux. I have a total of 6 Linux Servers, all integrated with Active Directory

All machines were working abosltely fine until recently and AD users were authenticating natively using LDAP on the Linux machines

One of our DomaiN Controllers needs to come offline to go over to our DR site

As soon as this server comes offline, 3 out of the 6 Servers stop allowing users to sign in with their AD accounts, and when logged on locally it takes ages to process any command

kinit commands still generate valid kereberos tickets on the affected machines, and getent passwd and other test commands still work as normal
The 3 Linux Servers simply won't allow users to logon anymore. The machines are configured identically to the 3 working machines!

The 3 affected machines simply won't allow users to logon using LDAP even though kereberos works fine. 
The ONLY was to resolve the issue is to power the offline Domain Controller back online. THen the 3 Linux machines work as normal with LDAP clients


This is a massive issue for me as i need this DC to be taken off site ASAP to Disaster Recovery

If anyone could provide any assistance with this issue it would be greatly appreciated

IS there any reason why the 3 affectred Linux machines, don't contact other DOmain Controllers when one is offline?
Is there anyway to force them to use specific DOmain Controllers?

It's such a strange issue, as there is aboslutely no direct reference to this DC on any of the affected Linux machines and they are configured identically to the 3 working Linux machines

Any help is greatly apreciatted
Willing to offer copious amounts of alcohol as a reward for the resolution of this issue! (and i'm deadly serious about that as this is a major issue for me)

Kind Regards

---

### Post by tomwoollard on 2009-03-16
I thought you might like to know that I have managed to resolve this issue, and it wasn’t anything to do with the ldap or Kerberos configuration on any of my Linux machines, which I thought would be the case seeing as my environment is completely uniform 

It's certainly a weird one and turned out to be an issue with the 3 faulty Linux machines residing on a separate VLAN to that of any of my Domain Controllers

It would appear that any Linux server not residing on the same vlan as any of my DC's would work absolutely perfectly until the last DC they contacted goes offline. A persistent connection appears to then be in place causing the machines to hang 

My identically configured Linux servers that were on the same vlan as the production DC's never had the above issue 

A netstat on the faulty Linux machines showed that they had connections to all of my DC's including the DR one 
A netstat on the working machines showed that they only had connections to the production DC's 


From this info I concluded that Linux openldap must contact DC's on the same vlan as the Linux host as a priority over all other authenticating ldap servers on the network 

I also noticed the arp tables were correctly populated with the prod DC's on the working machines whereas the faulty ones were not.
All of my Linux machines run on HP blades each with 6 NICS. I simply configured a spare NIC on each of the faulty Linux servers with an address on the same vlan where my prod dc’s reside and once I did, arp populated fully and they all dropped the redundant connections to the DR DC 


This DC can now be taken offline with the previously faulty machines authenticating as normal off of the production network

---

