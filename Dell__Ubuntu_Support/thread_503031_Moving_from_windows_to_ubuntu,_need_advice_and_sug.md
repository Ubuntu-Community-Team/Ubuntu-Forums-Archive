---
title: "Moving from windows to ubuntu, need advice and suggestions"
date: 2007-07-17
forum: Dell  Ubuntu Support
---

### Post by uforic on 2007-07-17
Hello all, I like some advice and suggestions on a complete move over to Ubuntu.

Here are the specs to my companies' Dell servers:
Dell PowerEdge 1850
2 x Intel Xeon 3.0GHz (EM64T)
2 x 1GB DDR2 400 SDRAM, ECC, registered
Integrated Single channel LSI53C1030 Ultra320 SCSI controller with 2 x 36GB 15k rpm Ultra320 SCSI Drives
Embedded ATI Radeon 7000-M with 16MB SDRAM video controller
Dual embedded Intel 82541EI Gigabit Ethernet NIC with PXE and WOL

In the process of ordering this for the 1850:
Optional embedded single channel Ultra320 SCSI integrated PERC 4e/Si with 256MB of battery-backed cache

Dell PowerEdge 2950
2 x Intel Dual Core Xeon 2.0GHz (5130-EM64T)
2 x 2GB DDR2 533 SDRAM, ECC, registered
Integrated PERC 5/i SAS 3.0 Gb/s RAID controller with 256MB of battery-backup cache with 4 x 73GB 15k rpm SAS Drives
Embedded ATI Radeon ES1000 with 16MB memory video controller
Dual embedded Broadcom NetXtreme IITM  5708 Gigabit Ethernet NIC with fail-over and load balancing.

Systems and platforms in these servers are as follows:
Dell 1850
-Apache
-php
-vsftp
-wordpress 2.2.1
-phpbb 2.0.22
-phpchat
-java irc
and looking at an opensource video and audio stream platform. Most probably with red5

Dell 2950
-Apache
-Mysql
-php
-vsftp
-postfix (for transport purposes only, low traffic)

What we have now are on windows 2003 server, obviously its become a headache for us and most importantly its become very unstable over the last year and half. Our setup is for a high traffic website with its focus on the phpbb forum and wordpress blog, all content of these 2 platforms are stored in mysql. And inside these 2 platforms, we provide live chat, java irc type chat and will start to provide streaming audio and video as well, also having these content stored in mysql. The postfix mail transport is mostly used in registration and newsletters to our members, therefore not a high traffic mail server.

Presently we are on only one PE1850 with all the services described minus the streaming part. So as you can see, its really taxing the server alot, so after researching and reading all the Dell server related post in Ubuntu forum, we decided to start preparing for a complete migration.

Here is our planning:
PE1850 - we will do a raid 0 on the present drives with a new PERC 4e/Si controller add-on. This will not only increase our drive space but also improve on the disk I/O. Its secondary gigabit ethernet port is use for database connection. 
PE2950 - We will do a raid 1+0 or raid 5 (but after doing all the research, for performance but with space sacrifices, we are leaning towards raid 1+0 but would like any advice from you guys, thanx)  this server main purpose is for Mysql and mail services. It will connect with our front end services like web, phpbb and wordpress via its secondary gigabit ethernet port. 

We are no experts by all means nor we are linux experience users, so any suggestions or advice to the above setup is much appreciated.

Here are my questions:
1. We are aiming for stabilities and readiness out of the box setup and really do not have the hacking expertise to make driver/hardware work properly, so I believe choosing Feisty Fawn 7.04 server edition is the best way to go, is this a correct move?

2. After reading all the posts in this forum, we have alot of worries regarding Dell's PERC raid controllers and Ubuntu driver supports. Since we need to do raid setup in both servers, are all these drivers ready out of the box, and getting everything to work like the we planned is going to work or we will face alot of issues?

3. I know the following are a bunch of old debates but my company is in China, 1. our techs/programmers are windows people, so gui environment is a must; 2. this is a world of kiddy hackers and virus infested environment, therefore all extra layer of protection and security are necessary. 3. our co-lo is quite a ways from our office, therefore a or a few remote management software are needed.
So here go my questions:
     1.	We will need a gui remote access, so we are going to install gnome in our servers and
         by using ssh and NoMachine’s NX servers, are there any security involved? There will be
         also all webmin that needs to be install as well, see any security issues in these?

     2.	Since we have all these remote access in the server, a firewall is a must; we looked at
         ubuntu-firewall and firestarter, which is better for our needs? Or are there any better
         ones?

     3.	I know this is much debated subject, is anti-virus needed in our setup? Our mail server is
         mostly outgoing mails, and very little incoming (at least we will ignore most of them) and
         we will not use pop, its all system emails.

4. We are a little confused about the support timeframe of each ubuntu distro, we read that LTS has longer support time, what does all these means to us? 

We really appreciate all advice and suggestion, and please excuse any dumb questions (as we are not familiar with linux) from here on, thank you in advance.

---

