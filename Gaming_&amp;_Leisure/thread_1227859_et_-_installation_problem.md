---
title: "et - installation problem"
date: 2009-07-31
forum: Gaming &amp; Leisure
---

### Post by Coonstantine on 2009-07-31
hello, I posted new thread because I found some just form 2005 and 06.
After I changed my computer I've got problems with installation of et. I know how to do it I suppose.. but I got always some errors.. :confused: like : mouse cursor flying around during the game. and if I'm trying to install true-combat-elite mode it installs somewhere else. :D 
have a look : 
> casper@casper-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

> casper@casper-laptop:~$ sudo lshw -C video
[sudo] password for casper: 
  *-display               
       description: VGA compatible controller
       product: RS780M/RS780MN [Radeon HD 3200 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

here i was trying to install enemy territory : 
> casper@casper-laptop:~$ cd Pulpit
casper@casper-laptop:~/Pulpit$ sudo ./et-linux-2.55.x86.run
sudo: ./et-linux-2.55.x86.run: command not found
casper@casper-laptop:~/Pulpit$ sudo sh et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
The setup program seems to have failed on unknown/glibc-2.0

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
casper@casper-laptop:~/Pulpit$ 
 I have no idea what's up this time... =/

---

### Post by Coonstantine on 2009-08-01
thank you very very much for your concern. problem solved ofcourse ;):confused:

---

