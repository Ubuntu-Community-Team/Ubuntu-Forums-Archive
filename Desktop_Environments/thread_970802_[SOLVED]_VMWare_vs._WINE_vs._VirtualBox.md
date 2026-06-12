---
title: "[SOLVED] VMWare vs. WINE vs. VirtualBox"
date: 2008-11-04
forum: Desktop Environments
---

### Post by akelsall on 2008-11-04
Hello, I have a few apps I need to keep Windows around for, so I'm looking for an easy, low resource way to run these Windows apps until I can find a Linux replacement. I'd like to hear the pros and cons people have about VMWare, WINE, and VirtualBox. Which is the easiest to set up and which uses the fewest system resources?

Thanks,

Andy

---

### Post by gregcss on 2008-11-04
what windows apps do you need to keep?

WINE emulates a windows directory structure that allows you to install some windows apps to that location. I only use this for pokerstars

VMWare emulates the windows operating system environment. I have not used this in linux but you should be able to install an windows app in the vmware instance of window

virtualbox - i have not used this

---

### Post by akelsall on 2008-11-04
The apps I still need to use are SnagIt (a screen capture program), Camtasia (a program to do screen recordings), and a VPN client I use to access my company's corporate network. I think the VPN client is going to be the hardest one to find a replacement for. 

Andy

---

### Post by CP1256 on 2008-11-04
I think Wine would do the trick with most simple programs, but as I'm browsing trough Wine DB ([http://appdb.winehq.org/](http://appdb.winehq.org/)) I see they rated Camtasia as 'garbage', so won't work with Wine. 

VMware is nice, but it emulates windows completely.

With Virtualbox you can run Windows programs 'seamless', meaning that Windows apps will look like normal Linux apps. 

Virtualbox didn't work out for me though, as it would hang during the Windows 98 installation. 

The best thing would be a dual-boot if you really need Windows apps.

---

### Post by warped6 on 2008-11-04
I use VirtualBox all the time. I have a couple programs for work that won't run in WINE and dual booting is not an option. I prefer VirtualBox over VMWare because it feels snappier plus I like the price. :-) I know there is a free version of VMWare too. 

Anyway.. I run XP in VirtualBox and use a Cisco VPN client to connect to one of my clients and it works flawlessly.

Just my 2 cents.

---

### Post by akelsall on 2008-11-07
Well, after doing some more research, I chose to use VBox, and I have to say it was a BREEZE. I thought it be a real headache, but it really wasn't it. I was able to install VBox, create a VM, and install Windows in under an hour. The installation of XP Pro only used up 1.5Gb of disk space. I highly recommend Virtual Box. 

Andy

---

