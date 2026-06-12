---
title: "[SOLVED] Reg:- Security of Linux"
date: 2008-12-29
forum: General Help
---

### Post by halovivek on 2008-12-29
Hi
I do have very great doubt in linux security from the hackers.
I use windows vista 64 bit as well as now Ubuntu 8.10 64 bit for my system.
1. I have configured windows with antispyware, anti malware, firewall and anti virus also. trusting on that one. I use to keep my system never switched off for 7-8 days until it asks for reboot or system becomes slow. so if you have all above you dont have to worry about the hacker since it cant be hacked easliy.
2. I dont have anti virus, anti malware in linux. I am planning to keep the ubuntu system as it is for some days. since i have rebooting un unnessarly. 

My doubts:-
1. How can i configure the firewall like windows. can you suggest me one. ( i use torrent to download movies, books to read)
2. how about the anti-virus, anti malware, anti spyware to linux.
3. if i keep the linux in the internet always on? how i will be protected from hackers.

please give a detail explanation to me.

---

### Post by mikewhatever on 2008-12-29
It's only too bad security problems are so rampant in Windows, however, Linux is not Windows, so it doesn't have to be that way. You'll need a different mind set to understand security in Linux. [Have a read.]("http://ubuntuforums.org/showthread.php?t=510812")
I used to be a frequent visitor to a Windows forum, where they still advise on the use of 'layered/realtime protection', which is similar to your setup. It made me wonder why couldn't a modern OS be reasonably secure out of the box, and why does a user need to spend hours of scanning the system for malware. I mean, windows users are so fortified with security programs, they can hardly use their computers.

---

### Post by 3rdalbum on 2008-12-29
1. How are you connected to the Internet? If you are connected through an ADSL modem/router (including a wireless network that has an ADSL internet connection) then you most likely already have a firewall inside the router, and there is no need to add another one.

Ubuntu has a firewall by default, but not switched on. You can install the program "gufw" to activate and configure the firewall.

Ubuntu doesn't listen on any ports, unless you install something that listens. If you're not listening to ports, you don't need a firewall anyway.

2. Anti-malware (including virus, adware and spyware) is not necessary on Linux, because there is no malware for Linux. This is due to the more secure design of the Linux system. Windows malware does not work on Linux unless you install Wine - even then most of it won't work, and none of it will be able to install itself without you actually double-clicking it.

3. If your system is not listening to any incoming ports, or if you have a firewall blocking all the ports, and you don't download software from any source that you don't trust, then you're protected from crackers.

If you want more of a description about the malware, then take a look at the Perminent Articles page on my website; there are a couple of in-depth things I've written there on the subject. Rest assured, the most secure computer systems in the world all run on Linux without an anti-virus program. Including the NSA, FBI, and Pentagon.

---

### Post by kokkus on 2008-12-29
As told above, you do not need that kind of security in linux.
There is a firewall that runs with startup in linux and it configures itself.
Since you have to enter a password for every admin action like installing, changing settings etc. there is no way a hacker can do changes on your system.
If you do have a virus on a file or something it really doesn't matter since in linux it won't take action at all.

There are some antivirus programs for linux but to scan windows files and emails.
When it comes to spyware you do not have to worry at all.

I have Ubuntu 8.10 and Winxp on my PC. I use XP only for a few things I can not use ubuntu for.
So as long as you use windows only when you really need to, you're PC is safe and will work fine in many years.

In windows you can get yourself more secure by not using internet explorer, replace the iexplorer.exe file with a empty useless file and use firefox as your default web browser.

---

### Post by scorp123 on 2008-12-29
> **halovivek said:**
> I do have very great doubt in linux security from the hackers.  Are you running a server? e.g. a mail server, web server, FTP server, or anything like that? If not you're most likely not even an interesting target for a hacker :D

> **halovivek said:**
>  I dont have anti virus, anti malware in linux.  And there is no need to. Virus scanners on Linux mostly scan for Windows viruses anyway. So those programs only make sense if you are running a file server which gets accessed by Windows machines too. As a home user you could safely live without one and use the free RAM and the free CPU cycles for other things.

> **halovivek said:**
>  How can i configure the firewall like windows. Again: are you running any services on your Linux and if so: which ones? Per default and "out of the box" there are no running services on Ubuntu. And therefore there is no need for a Firewall! :D  What is a firewall supposed to protect when there is absolutely nothing that would need such protection??

Windows is "out of the box" running many highly unsafe network services, but instead of fixing that behaviour Microsoft came up with that firewall (which is not quite perfect too). So on Windows you indeed need a firewall because you're indeed at risk otherwise.

> **halovivek said:**
>  how about the anti-virus See above. If you absolutely think you have to use one, well then, grab these packages: 
[LIST]
[*]clamav
[*]clamav-freshclam
[*]nautilus-clamscan
[/LIST] ... the last package adds a "Scan this file ..." option to the "Nautilus" file manager.

> **halovivek said:**
>  anti malware I am not aware of such packages. But then again it's rather hard to be infected with malware in the first place :D  Simply put: never ever install anything from unknown sources, e.g. always use the package manager and the software it offers you, don't download stuff from web sites you don't know. Ask here if in doubt.

> **halovivek said:**
>  anti spyware to linux.  Same as above. It's quite hard to be in any way infected with such things on Linux in the first place. Not entirely impossible though ... but as home user you are unlikely to get in contact with such things. As a server admin you should pay attention to what your users are doing and you'd here and there have to scan for so called "root kits", but that's an advanced topic and not something you will likely ever get into contact with, IMHO.

> **halovivek said:**
>  if i keep the linux in the internet always on?  Don't you have a DSL- or cable router or something? Doesn't it already have firewall functionality?

> **halovivek said:**
>  how i will be protected from hackers. As long as you are not running any services on your Linux installation (and that would be the default on Ubuntu "out of the box") there is not even anything a hacker could remotely connect to ... So what do you need protection against? A wannabe hacker can't even reach you (except with "ping" maybe?) in the first place, for as long as you are not installing anything that would open up a networked service.

---

### Post by Greyed on 2008-12-29
> **scorp123 said:**
> What is a firewall supposed to protect when there is absolutely nothing that would need such protection??

To be fair one thing that the Windows firewalls do is protect against outbound traffic as well.  Most Linux solutions default to DENY on the inbound but ALLOW for the outbound.  Granted one can set outbound to DENY but providing exceptions on the Linux side is horrible by comparison.

> Don't you have a DSL- or cable router or something? Doesn't it already have firewall functionality?

If they do they probably have the most effective form of firewall, NAT.  Though most people don't recognize NAT as a firewall in function.

---

### Post by halovivek on 2008-12-29
i will check whether i do have router in between the internet connection of the provider and i will get back to you. i am going through what are all say. thanks

---

### Post by scorp123 on 2008-12-29
> **Greyed said:**
> To be fair one thing that the Windows firewalls do is protect against outbound traffic as well.  Yes, but are you aware of why it is so? :D  Because Microsoft are very well aware of the fact that still too many users are working with admin rights and are therefore likely to catch malware. Some of the malware "out there" by itself is harmless, they need to load the actual harmful "payload" from a server. Many worms function like this. And that's why their firewall de facto has to check outbound traffic too in order to minimise the effects of malware, spyware and trojans trying to "phone home" and download more of the harmful stuff ...

I can imagine one use why you would want to do this nontheless: parental control, e.g. keep your children away from web sites they should not (yet) surf to. But there are many ways to achieve this (e.g. manipulate the /etc/hosts file), blocking outbound traffic with a firewall seems a bit like overkill to me, IMHO.

> **Greyed said:**
> If they do they probably have the most effective form of firewall, NAT.  Wrongly configured port forwardings can easily defeat NAT. NAT is only safe if you don't let any services into your network.

> **Greyed said:**
>   Though most people don't recognize NAT as a firewall in function. There are good reasons to this :D  NAT is in no way the same thing as a packet filter, and a packet filter is not the same thing as a fully stateful firewall :D

---

### Post by halovivek on 2008-12-31
Thank you so much for all for valuable reply.

---

