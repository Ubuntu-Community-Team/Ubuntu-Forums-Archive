---
title: "Is (K)Ubuntu really enterprise ready?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by kitts_82 on 2006-06-17
Hello everyone. I have been using Kubuntu for a year now but have only now joined this forum. I absolutely love this this distribution and have promoted it to many people. Of whom, currently,  at least 10 use it exclusively.

Beyond using it personally, i have fought for it and have had it installed to dual boot on my machine at work this week. Here is where i faced issues that made me think on the lines of this posts subject line.

This is a great distro for the home users and *can* be made to be one in the corporate world as well, but has no easy way of doing it.

Among the first issue i faced is with apt. We use a proxy with authentication in office and i couldn't get apt to update. I have tried all the help i could find from these forums but was unable to pass the authentication (Its an ISA server; this is still a problem but that's another thread). Even worse is the fact that the installer tries to connect to the net during installation. This is not always a bad idea but can be in cases like the above. Apt would seem to wait forever and it would seem like the installation has hung. I then had to disable the network interface and then the installation would progress.

I would have expected the installation process asking me if it should connect to the internet to get the latest security updates!

Second, though not a problem, i would expect the installer to offer options for installation of grub.

The first is directly connected to the subject of this post. Beyond that, i would an enterprise distribution to offers features common to many corporate offices.

1) Enterprise editions allow logins based on those offered by a server. So that way username/passwords remain common to connecting to the proxies, mail servers, etc apart from the desktop. And when once someone modifies passwords to their desktop, the same is updated on the server. There is no easy and straight forward way to configure the system to work this way.

2) Groups of users need to exist with varying privileges. These groups are to be defined on the server, and ever user shall belong on of the groups.

3) Software distribution - This will need some automation. Although users can install software of choice some packages *have* to be installed and shall be updated on all machines in the network on server command.

4) Laptops - They are mobile and users hop networks when using them. There needs to be ways to facilitate that. And also to securely connect to the company server from outside the company and appear as part of the local network.

An extention of the last point is also applicable to the general home users. Networking happens from either wired 10/100/1000 network or wireless lan. Internet connectivity is through this network or dialup. There needs to be easy ways to shift connections for local network browsing and internet connectivity.

I know that all of the above must be possible to setup but i was unable to find an easy setup. May be someone with the knowledge and experience can prepare guides and/or how-to's that explain how to setup the server and the client for the job.

With that said, this is still a great distribution! Kudos to all the developers and all those who help out on these forums. =D>
-
kitts

---

### Post by raptros-v76 on 2006-06-17
as to number 4, ubuntu is far better for my laptop than even the windows that shipped with it

---

### Post by fluffington on 2006-06-17
[QUOTE=kitts_82]I would have expected the installation process asking me if it should connect to the internet to get the latest security updates!

Second, though not a problem, i would expect the installer to offer options for installation of grub.[/QUOTE]

Should have used the expert text-mode installer on the alternate or server CD (depending on whether you were installing to a desktop or server). The graphical and non-expert installers are dumbed down for people who don't need all the extra options.

[QUOTE=kitts_82]4) Laptops - They are mobile and users hop networks when using them. There needs to be ways to facilitate that. And also to securely connect to the company server from outside the company and appear as part of the local network.

An extention of the last point is also applicable to the general home users. Networking happens from either wired 10/100/1000 network or wireless lan. Internet connectivity is through this network or dialup. There needs to be easy ways to shift connections for local network browsing and internet connectivity.[/QUOTE]

I've never seen any OS handle wireless roaming well, Windows and Mac included. A quick [Google search](http://www.google.com/search?q=ubuntu+wireless+roaming) turned up the following, though:

[list]
[*][O'Reilly Ubuntu Hacks book](http://www.oreilly.com/catalog/ubuntuhks/) ("... learn the ins and outs of ... wireless roaming ...")
[*][CLUG Wiki: Roaming between wireless and wired](http://wiki.clug.org.za/wiki/Roaming_between_wireless_and_wired)
[*][QuickSwitch Profiler](http://sourceforge.net/projects/quickswitch/)
[/list]

Note that I haven't used wireless on Linux in a very long time, so I have no idea how well those work or if there are any better solutions out there.

---

### Post by raptros-v76 on 2006-06-17
there are several good wireless roaming applications for kubuntu. like kwifimanager, which does scanning and connecting and stuff.

---

### Post by kitts_82 on 2006-06-18
[QUOTE=fluffington]
[QUOTE=kitts_82]
I would have expected the installation process asking me if it should connect to the internet to get the latest security updates!
 
 Second, though not a problem, i would expect the installer to offer options for installation of grub. [/QUOTE]

 Should have used the expert text-mode installer on the alternate or server CD (depending on whether you were installing to a desktop or server). The graphical and non-expert installers are dumbed down for people who don't need all the extra options.
 [/QUOTE]

I used the text mode installer at home. But chose to use the graphical installer just to demonstrate to people that it was easy to setup linux. Even with the text mode i had the same problem. I am connected to broadband internet and have unlimited download so i let it progress but i found no way to avoid updating during install unless i had the cable unplugged. :-(

[QUOTE=raptros-v76]there are several good wireless roaming applications for kubuntu. like kwifimanager, which does scanning and connecting and stuff.[/QUOTE]
I do not have any personal experience with wireless networks under linux hence i am poorly informed. Does kwifimanager serve the purpose of managing both local network browsing and internet connectivity?

---

### Post by sgla1 on 2008-04-08
> **kitts_82 said:**
> 
 Beyond that, i would an enterprise distribution to offers features common to many corporate offices.

1) Enterprise editions allow logins based on those offered by a server. So that way username/passwords remain common to connecting to the proxies, mail servers, etc apart from the desktop. And when once someone modifies passwords to their desktop, the same is updated on the server. There is no easy and straight forward way to configure the system to work this way.
-
kitts

All enterprise-ready distros make it easy to configure server-based logins during install.  Imho this is an absolute requirement for use in the enterprise.  Having this be totally absent in Ubuntu tells me Canonical views their market as home users.  This is too bad as there is much to recommend Ubuntu.

All enterprise-ready distros also provide extensive, well written and QA'd documentation.  They don't depend on community volunteers to write their docs, even if many of them are very good.

I just spent several days figuring out how to configure an openldap server/client authentication setup.  The Ubuntu documentation is lacking and in some places flat-out wrong.  I used multiple sources, tailed logs and experimented quite a bit.  

I'm a professional Unix sysadmin, even though I am new to ldap.  As a general rule I am going to pick the distro that can be configured quickly because I do not have unlimited time to tinker.  If Ubuntu wants to become a player in the enterprise market that is something they have to keep in mind.

Steve G

---

