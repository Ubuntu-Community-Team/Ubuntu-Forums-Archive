---
title: "UNIX command translation"
date: 2006-09-08
forum: Desktop Environments
---

### Post by froggay on 2006-09-08
hello,
I found some unix transaltion table on google
ie:[http://www.opennet.ru/soft/linux2unix.html]("http://www.opennet.ru/soft/linux2unix.html")

but nobody seems to made one with ubuntu or debian.

does someone know where i can find a summary of command for commons tasks on ubuntu ?

---

### Post by ayoli on 2006-09-08
depends of what you're looking for but basic commands such as ls, lsmod, cat, df, etc... are the same on all distribs.
specific commands for ubuntu/debian are apt-get, aptitude, also specific locationsch as /etc/rc[0:6].d/ for boot scripts.

---

### Post by Lord Illidan on 2006-09-08
The article was a bit confusing. Too many commands on one page!!

[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

[http://www.tldp.org/HOWTO/Text-Terminal-HOWTO.html](http://www.tldp.org/HOWTO/Text-Terminal-HOWTO.html)

---

### Post by froggay on 2006-09-08
[quote=ayoli]depends of what you're looking for but basic commands
[/quote]Well the aim is to keep the same structure of the file linked on first thread.

So for example all the section regarding software should be specific to ubuntu.

And some basic tasks like :
 - change or set static ip, gateway, dns
 - change hostname
 -...

could be described .

So if people can help me translate some chapter, i will make all the sheet

[quote=Lord Illidan]The article was a bit confusing. Too many commands on one page!![/quote]

yes it's a big page , but it's interesting, you can quickly find a keyword by ctrl+f 

And thank you for the links ! very interesting

---

### Post by ayoli on 2006-09-08
change ip use ipconfig , change gateway use route and so, they are basic linux commands not specific to ubuntu.
edit: have a look here:
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)
and here:
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

---

### Post by froggay on 2006-09-08
> **ayoli said:**
> change ip use ipconfig , change gateway use route and so, they are basic linux commands not specific to ubuntu.


well, i don't have "ipconfig" on ubuntu 6.06, i suppose it's ifconfig.
usually to do this tasks i edit /etc/networks/interface file , is ther a better way ?

---

### Post by ayoli on 2006-09-08
> **froggay said:**
> well, i don't have "ipconfig" on ubuntu 6.06, i suppose it's ifconfig.
usually to do this tasks i edit /etc/networks/interface file , is ther a better way ?

my bad :) i wanted to say ifconfig
you can edit /etc/networks/interface, or use ifconfig + route or use the graphical way (menu System > Administration > Network then you 'll be prompted for user password)

---

### Post by tuxinvader on 2006-09-08
The ip command is valid, you don't want to replace it with ifconfig. Thats like suggesting nslookup over dig or host. Ifconfig is old and creaking and it doesn't support a large chunk of the newer networking features in linux. ip will eventually replace ifconfig and route altogether.

---

