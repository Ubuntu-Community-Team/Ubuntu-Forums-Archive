---
title: "Adding virtual ip in Ubuntu 11.10"
date: 2011-11-08
forum: Desktop Environments
---

### Post by call_krushna on 2011-11-08
Hi Everybody,

        I want add virtual ip for my pc(Ubuntu 11.10).I have edited the file
#vi /etc/network/interface             and added the below line

auto eth0
iface  eth0 inet static
      address 192.168.0.190
      netmask 255.255.255.0
      broadcast 192.168.0.255
      gateway 192.168.0.8
auto eth0:1
iface  eth0:1 inet static
      address 192.168.0.41
      netmask 255.255.255.0
      broadcast 192.168.0.255
      gateway 192.168.0.8

But while restarting the network service gives the below error

[COLOR=Red][FONT=Courier New][B]Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                         RTNETLINK answers: File exists
Failed to bring up eth0:1.[/B][/FONT][/COLOR]

Any suggestion highly appreciated .

Thanks in advance
                                                                                                                   
                                   [URL="http://www.linuxquestions.org/questions/report.php?p=4518990"]
[/URL]

---

### Post by bluexrider on 2011-11-08
Did you uninstall your network manager?


add virtual IP the easy way
[http://www.liberiangeek.net/2010/02/creating-virtual-ip-addresses-in-ubuntu-the-easy-way/](http://www.liberiangeek.net/2010/02/creating-virtual-ip-addresses-in-ubuntu-the-easy-way/)

---

### Post by call_krushna on 2011-11-09
Sorry to say this,

              I have already followed the url earlier and it was working with Ubuntu 10.04. Problem started with 11.10 .Sorry for posting the stupid question .but I am not able to get solution around .

---

### Post by chakhedik on 2011-12-06
Hi,

I face exactly the same problem with ubuntu 11.10...it works fine with 11.04 then it failed tu bring up after upgrade to 11.10...have you found the workaround?

---

### Post by flickerfly on 2011-12-08
This link looks like it has relevant information:
[http://www.linuxquestions.org/questions/linux-networking-3/rtnetlink-answers-file-exists-error-when-doing-ifup-on-alias-eth1-1-on-rhel5-710766/](http://www.linuxquestions.org/questions/linux-networking-3/rtnetlink-answers-file-exists-error-when-doing-ifup-on-alias-eth1-1-on-rhel5-710766/)

I've found that even though I can't see the virtual NICs they are responding. In that link, the OP mentions "Further read indicated there is an option for alias files to start the alias interface at same time as primary or not. The default is to start at same time." Anyone have a clue how to change that?

---

### Post by call_krushna on 2011-12-14
> **chakhedik said:**
> Hi,

I face exactly the same problem with ubuntu 11.10...it works fine with 11.04 then it failed tu bring up after upgrade to 11.10...have you found the workaround?


_[Hi chakhedik]("http://ubuntuforums.org/member.php?u=996901")_

     Still I am waiting for solution .

---

### Post by SeijiSensei on 2011-12-14
This is a [known bug in 11.10](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/876829).

You could create the interface manually in /etc/rc.local.  Remove the definition in /etc/network/interfaces, then edit /etc/rc.local and add this command:

```

ifconfig eth0:0 192.168.0.41 netmask 255.255.255.0 broadcast 192.168.0.255
```

You don't need a gateway directive; the aliases always use the same gateway as the physical adapter.

---

### Post by flickerfly on 2011-12-14
That report says a fix was released last month, but I'm still having the problem. When should we expect that to trickle into the repos?

---

### Post by chakhedik on 2011-12-16
> **SeijiSensei said:**
> This is a [known bug in 11.10]("https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/876829").

You could create the interface manually in /etc/rc.local.  Remove the definition in /etc/network/interfaces, then edit /etc/rc.local and add this command:

```

ifconfig eth0:0 192.168.0.41 netmask 255.255.255.0 broadcast 192.168.0.255
```You don't need a gateway directive; the aliases always use the same gateway as the physical adapter.

thanks SeijiSensei, that solve my problem....thank you very much :D

> 
That report says a fix was released last month, but I'm still having the  problem. When should we expect that to trickle into the repos?i think the fix released for debian only and not yet been pushed to ubuntu....

---

### Post by call_krushna on 2011-12-22
> **SeijiSensei said:**
> This is a [known bug in 11.10]("https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/876829").

You could create the interface manually in /etc/rc.local.  Remove the definition in /etc/network/interfaces, then edit /etc/rc.local and add this command:

```

ifconfig eth0:0 192.168.0.41 netmask 255.255.255.0 broadcast 192.168.0.255
```You don't need a gateway directive; the aliases always use the same gateway as the physical adapter.

[Thanks a ton SeijiSensei]("http://ubuntuforums.org/member.php?u=698195")   for the solution .This resolved my problem .I was about to downgrade OS .Sorry for late reply .

---

### Post by call_krushna on 2011-12-22
Thanks a lot .

---

