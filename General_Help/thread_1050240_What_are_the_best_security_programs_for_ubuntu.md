---
title: "What are the best security programs for ubuntu?"
date: 2009-01-25
forum: General Help
---

### Post by tomjay725 on 2009-01-25
1. im going to be installing ubuntu on my desktop and i know it says you dont "need" security but i want it just in case. What are the best firewall, maleware and antivirus programs for it?

2. also where can i get all my drivers for my printer(canon pixma 480) as well as sound video dvd drivers etc

thanks!!

---

### Post by taurus on 2009-01-25
1.  People use firestarter and it should be avaiable from the repos (synaptic, add/remove, or apt-get/aptitude).  You don't need anti-virus for Linux.

2.  Just install it and configure your printer.  Changes are Ubuntu comes with a driver for your printer.  And for your soundcard and DVD, they should just work.  However, what kind of soundcard do you have?

---

### Post by jrusso2 on 2009-01-25
I would say SE Linux is you can figure out how to set it up.

---

### Post by sisco311 on 2009-01-25
> **tomjay725 said:**
> 1. im going to be installing ubuntu on my desktop and i know it says you dont "need" security but i want it just in case. What are the best firewall, maleware and antivirus programs for it?

2. also where can i get all my drivers for my printer(canon pixma 480) as well as sound video dvd drivers etc

thanks!!

The best security "program" for ubuntu and linux in general is the user. If you update your system regularly  and don't install programs from untrusted sites you should be safe.

Check this links (security and security tools):
[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")
[https://help.ubuntu.com/community/Security]("https://help.ubuntu.com/community/Security")

Can you post your system specs?

---

### Post by tjwoosta on 2009-01-25
antivirus is not necessary for the sake of your linux box, but if you are networked with, or come in contact with, windows PC's often you should consider running an antivirus once in a while to prevent spreading viruses to them

i use clamav


you should not need a firewall tool unless you are running a server of some sort, because by default your linux does not have any open ports

if you are infact running a server of some sort i would suggest manually configuring iptables (just so you can learn what is really happening behind the scenes with firestarter)

the archlinux wiki has a very good read on configuring iptables that is not necessarily distro specific and what you learn there should work almost the same with Ubuntu (aside from the package management commands obviously)

[http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO]("http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO")

also here is some of the official ubuntu documentation

[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

---

### Post by tomjay725 on 2009-01-25
not sure but the cd that came with it is sound blaster live by creative. im installing linux now ill check the driver when its done

---

### Post by tomjay725 on 2009-01-25
my system specs are pentium 4 2.6 ghz 1.5 gbs of ram 120gb hard drive

---

### Post by tomjay725 on 2009-01-25
also my favourites are url files and firefox cant import them because their not html format, does ne one have a convertor for that? (url to html)

---

### Post by cariboo on 2009-01-25
The best way to check if your hardware is supported is to boot from the LiveCD and make sure everything works. As for security as was stated earlier, the most danger to your installation is the user. Here are a couple of links on security:

[Ubuntu Intrusion Detection]("http://ubuntuforums.org/showthread.php?t=919472")

[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

The main things is to have strong passwords and do smart browsing.

Jim

---

### Post by adamlau on 2009-01-25
chown, chmod, netstat, nmap, gpg, /etc/fstab, /etc/sysctl.conf, AppArmor. Focus on the simple stuff :) .

---

### Post by Tomatz on 2009-01-25
If you have a physical firewall (router), you will not need to install firestarter. As a router/firewall does the same job but IMO better.

Go here to run tests to see how secure you really are:

[http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)

I pass all tests with a cheap belkin router ;)

---

### Post by Tomatz on 2009-01-25
I just ran a test on the first 1056 ports of my OS. As you can see, to a hacker they just wouldn't exsist.

---

