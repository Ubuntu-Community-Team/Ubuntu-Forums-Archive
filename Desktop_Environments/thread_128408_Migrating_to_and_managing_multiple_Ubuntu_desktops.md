---
title: "Migrating to and managing multiple Ubuntu desktops"
date: 2006-02-11
forum: Desktop Environments
---

### Post by MrDez on 2006-02-11
I have inherited a network that is a mess of Xandros 3 Pro desktops, a windows terminal server, and an xDMS server.  I have installed a single ubuntu workstation as a comparison to side-by-side demo it vs. Xandros, joined it to the windows domain and enabled kerb authent, and Ubunut blows it out of the water in terms of overall speed and reliability.  Ubu running on a p3 700 vs Xandros on a p4-2.4ghz is still much more responsive and feels much more stable.  The company is having nothing but trouble with Xandros, even on their newest machines. (Xandros networks is a slow, useless nightmare).  At this point, its either get ubuntu working and manageable across the company or go back to Windows (which all of the machines have their own OEM licenses for anyway).  The company is still willing and open to the idea of sticking with linux, but patience is wearing thin thanks to so much trouble with Xandros.

The real crux of my issue is identifying the best way to manage multiple desktops AND manage deployment of new installs or redeployment of existing but damaged installs.  I primarily support windows only networks but have personally run linux for years, but never supported it beyond a small workgroup of machines.  Am I correct to speculate that the more cost effective way to approach this problem is simply with webmin for desktop management and customizing OEM ub installations by hand?  Suggestions,  links. and any and all suggestions (espcially pointing me where to RTFM) are all welcomed.

Thanks,
MrD

---

### Post by mjfleck2000 on 2006-02-11
How many desktops are you going to manage?

I am the "network admin" of a small network, 25 Windows desktops and 10 Ubuntu desktops, with Debian servers at two seperate locations.  To manage the Ubuntu desktops, I use a combination of ssh and Freenx.  With such a small number of desktops, this works very well.  

Mike

---

### Post by chele on 2006-02-11
Would the Terminal Server from Edubuntu be useful in this type of environment?

---

### Post by MrDez on 2006-02-11
[QUOTE=mjfleck2000]How many desktops are you going to manage?

I am the "network admin" of a small network, 25 Windows desktops and 10 Ubuntu desktops, with Debian servers at two seperate locations.  To manage the Ubuntu desktops, I use a combination of ssh and Freenx.  With such a small number of desktops, this works very well.  

Mike[/QUOTE]

This particular client has ~30 linux desktops, 2 win2k desktops at primary site, and 5 satellite offices (connected by vpn) with 2-10 desktops (most pending conversion to linux) each.

Im not particularly referring to remote desktop control or even ssh,  I'm really trying to get a feel for any potential automated sitewide patch and configuration management tools, basically a webmin from one central location that can manage all machines, possibly including things like updates, network configurations, hardware inventory, log and error reports, and general tech maintenance.  I've been transferred full control of the sites IT support and maintenance, but they are not my only client and I need SOME level of automation to keeps things smoother.

Thanks,
Matt

---

### Post by MrDez on 2006-02-11
Windows Terminal server is needed becuase the primary app used by the client is windows only (will not work with wine despite hours upon hours of fighting with it).

---

### Post by cwaldbieser on 2006-02-11
[QUOTE=MrDez]This particular client has ~30 linux desktops, 2 win2k desktops at primary site, and 5 satellite offices (connected by vpn) with 2-10 desktops (most pending conversion to linux) each.

Im not particularly referring to remote desktop control or even ssh,  I'm really trying to get a feel for any potential automated sitewide patch and configuration management tools, basically a webmin from one central location that can manage all machines, possibly including things like updates, network configurations, hardware inventory, log and error reports, and general tech maintenance.  I've been transferred full control of the sites IT support and maintenance, but they are not my only client and I need SOME level of automation to keeps things smoother.

Thanks,
Matt[/QUOTE]

You could have a script that used ssh to execute commands on each of the remote computers.  For example, say you had a local repository cache set up, and you wanted to have each of the computers on the network get the latest security updates.  You could have a script that iterates over each PC's ip address or hostname, log in using ssh, and pipe the apt-get command(s) to do the updates on each PC.

---

### Post by MrDez on 2006-02-11
[QUOTE=cwaldbieser]You could have a script that used ssh to execute commands on each of the remote computers.  For example, say you had a local repository cache set up, and you wanted to have each of the computers on the network get the latest security updates.  You could have a script that iterates over each PC's ip address or hostname, log in using ssh, and pipe the apt-get command(s) to do the updates on each PC.[/QUOTE]


I considered some mad mass of cron jobbed scriptfu-ness, but I need to be able to transfer maintenance of the site to another tech as needed, and right now I'm the only command line friendly tech in sight, and I'd rather stick with a web based solution.  I may end up writing some kind of psuedo webmin module, but time is tight atm and I was hoping for a ping on something that can handle a good bit of automation with minimal work.  

Most likely, I'm just too spoiled on the 'easy' stuff after spending years managing so many windows networks.

Thanks,
Matt

---

### Post by az on 2006-02-11
[QUOTE=MrDez]I was hoping for a ping on something that can handle a good bit of automation with minimal work.  

Most likely, I'm just too spoiled on the 'easy' stuff after spending years managing so many windows networks.

Thanks,
Matt[/QUOTE]
The strength of debian based distros is the package management system.  Most of what you want to automate (patching, customisations, repairs and security updates) is already package-centric.

You make your own private repository and manage the packages within it.  All boxes only use that repository for stuff, so as soon as you throw new packages into it, they install them (you make then get their updates frequently).

It requires rudementary packaging skills, but you can get your boxes to do anything like that.

---

### Post by mjfleck2000 on 2006-02-27
[QUOTE=MrDez]This particular client has ~30 linux desktops, 2 win2k desktops at primary site, and 5 satellite offices (connected by vpn) with 2-10 desktops (most pending conversion to linux) each.

Im not particularly referring to remote desktop control or even ssh,  I'm really trying to get a feel for any potential automated sitewide patch and configuration management tools, basically a webmin from one central location that can manage all machines, possibly including things like updates, network configurations, hardware inventory, log and error reports, and general tech maintenance.  I've been transferred full control of the sites IT support and maintenance, but they are not my only client and I need SOME level of automation to keeps things smoother.

Thanks,
Matt[/QUOTE]

Matt, 
Your question prompted me to look at the way I am now handling my setup.  I have (at this time!) about 20 Windows desktops and  15 Linux desktops in two seperate locations.  I have been using ssh to go to each Linux machine to do any updating/maintenance/repair (For the Windows machings, I use VNC).  
I now have a part-time assistant that will help out when I have other duties (like payroll!), sick or vacation.  I am starting her out with the command line  but I will also use GUI tools.
So, I have, for the last week, started using Webmin again.  Webmin has a "Cluster" module that allows actions to be taken across a group of computers.  Using Webmin, I can update programs, uninstall programs, set up cron jobs, set up Group Cron Jobs (think update packages), Firewalls,add/del users, change passwords/setup Samba, etc.

I also started using, again, Nagios.  If you are not familiar with Nagios it is a web based mointor of computers and services running on computers.  

Occasionally, I use VNC or NX to help set up the desktop for someone.

This all has worked very well managing the various computers from my own personal desktop running Ubuntu. My fall back is, of course, ssh.

Webmin [http://www.webmin.com](http://www.webmin.com)
Nagios   [http://www.nagios.org](http://www.nagios.org)
VNC      [http://www.realvnc.com](http://www.realvnc.com)
NX        [http://www.nomachine.com](http://www.nomachine.com)
All of these should be  available with apt-get.

Hope this is of some help.

Mike

---

