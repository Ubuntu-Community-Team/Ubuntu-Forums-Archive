---
title: "Hacking Competition Help"
date: 2009-04-03
forum: General Help
---

### Post by diggis_tennis on 2009-04-03
Hello friends,

I am a newbie with Linux and similar OS. I am taking this course in my MS degree which involves a hacking competition. I was wondering if any one can help with it. The following are the details of the competition.

Introduction

The purpose of this lab is two fold: harden an install of Ubuntu 7.04 Desktop (Linux) and to compromise other computers on the lab network. Points will be assigned according to the level of compromise achieved on other boxes. A report will be required on Wednesday, April 16th for a grade and a bonus given for a high score during the competition. There will be two in-lab competitions: April 6th and 8th. On each date, all teams will be given one hour concurrently to attempt to compromise the other computers including the other teams.
Network Setup

The competition will take place on a private network. There will be some vulnerable machines (henceforth called victim boxes) and a hardened machine on the network in addition to the students' machines (called team boxes). The hardened box and the victim boxes will be randomly generating connections to each other and to the team boxes. The network is in no way connected to any outside network, so any data you may want will have to be brought in by other means. The primary subnet for the competition is 192.168.100.0/24
Hard Drive and Machine Access

Each team captain will receive a hard drive in class, which will have to install a Ubuntu 7.04 Desktop (Linux), running several services prescribed below. Each team will be assigned an IP address. You can plug the hard drive into any unused Dell Dimension 370 systems in KACB 2446. You will need a hard drive lock key for it to work. The hard drive has a serial IDE interface and may not work with many older systems. You may take the hard drives home to install patches or whatnot. All teams and victims should be configured to use the 192.168.100.0/24 network.
User Accounts

A user account called "hacker"&#65533; should be created on each team box. Each team must pass the login information of that account to Chris and its password should not be changed throughout the competition. This account is used to test the services with the traffic generator, thus accurate login information is vital. Each team member should have their own logins into the system as well.
Services

During the competition, each server should have all services available listed in the table below. Each service must be on the default port listed and must allow a valid login from any computer on the network. This will be tested by traffic generating scripts from random source IPs. These services should be maintained throughout the duration of the competition. SMTP should not relay, but should deliver email from anywhere to users on the box.
Service 	Port
ssh 	22
telnet 	23
smtp 	25
https 	443
MultiCastZoo 	446
phpMyAdmin 	/pma
mysql* 	3306
XMPP/Jabber 	5222

* MySQL does not have to be available via the network, but the contents should be accessible via the webpage interface, phpMyAdmin.
Goals

Points are assigned by the level of compromise each team is able to perform to the network. Do note that efficiency and creativity are given bonuses (but it's impossible to outline them here). We want people to think up and implement new ways of exploiting machines and will reward such efforts in any way we can.

The target goals and points provided for each in this competition are as follows:

    *
      Mapping the network (2 pts. per ip)
    *
      Mapping services (20 pts. per box)
    *
      OS detection (10 pts. per victim box)
    *
      Gaining user access to a victim box (30 pts.)
    *
      Gaining user access to a team box (50 pts.)
    *
      Gaining root access to a victim box and retrieving the shadow hash file (150 pts.)
    *
      Gaining root access to a team box and retrieving the shadow hash file (250 pts.)
    *
      Time bonus: Additional points given for time to complete all of the above goals according to the time table below.
    *
      Not having services up during competition (-150 pts.)
    *
      Your box becomes compromised (-300 pts.)

Below are bonuses you can receive outside of the competition:

    *
      Super bonus: successfully cracking a password (100 pts. per password). You can continue to crack passwords up until the turnin deadline.

Time Frame 	Bonus
0~5 (min) 	200
5~10 	150
10~15 	100
15~20 	50
Rules

In attempt to keep the competition clean yet creative, a few simple rules should be observed.

   1.
      Attackers should not change victims' passwords unless needed for a compromise, and then it should be reset back to the original password.
   2.
      No denial of service attacks, rate throttle your nmaps (no -T4).
   3.
      Services on the team and victim should remain up and active throughout the competition. Services should not be turned off by the defender or the attacker (unless momentarily necessary for a compromise or defense). The service should still be available for legitimate use.
   4.
      Absolutely no deleting of logs. They are precious as gold when writing the report.
   5.
      No Arp poisoning this year, we will use a hub. Since we have eight teams we cannot support all teams doing arp poisoning.

---

### Post by kanikilu on 2009-04-03
Sorry to be blunt, but first of all, people are here to help others with real problems, not do your homework for you :rolleyes:

Secondly, a lot what you're asking involves talking about things that are not allowed on this forum, as far as I know (e.g. gaining root access - esp. with regards to a system that is not yours, even if it is for "education", or in this case, a competition...).

---

### Post by Godly on 2009-04-03
> **kanikilu said:**
> Sorry to be blunt, but first of all, people are here to help others with real problems, not do your homework for you :rolleyes:

Secondly, a lot what you're asking involves talking about things that are not allowed on this forum, as far as I know (e.g. gaining root access - esp. with regards to a system that is not yours, even if it is for "education", or in this case, a competition...).
And there you have your answer.

---

### Post by Rocket2DMn on 2009-04-03
As has been pointed out, we don't do homework help here.  Good luck.

---

