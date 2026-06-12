---
title: "VMware + XP + Bridged network = No Interernet"
date: 2006-07-25
forum: Desktop Environments
---

### Post by tomasmekean on 2006-07-25
Can so one please help me.

my network adapters are eth0(wired) & eth1(wireless) both are bridged and for some reason I get....  

This connection has little or no connectivity.  You might not be able to access the internet or some network resources....

Worked fine under SuSE 10.0 & 10.1 however ubuntu said Hell no.... 

Anyway please help if you can.  I like ubuntu and would like to keep installed.  However I have to use xp for some work issues that rdesktop just can't solve.  

Thnx in advance...

Tomas

---

### Post by tomasmekean on 2006-07-26
am I the only one having this problem??????

---

### Post by jgmitchell on 2006-07-27
> **tomasmekean said:**
> Can so one please help me.

my network adapters are eth0(wired) & eth1(wireless) both are bridged and for some reason I get....  

This connection has little or no connectivity.  You might not be able to access the internet or some network resources....

Worked fine under SuSE 10.0 & 10.1 however ubuntu said Hell no.... 

Anyway please help if you can.  I like ubuntu and would like to keep installed.  However I have to use xp for some work issues that rdesktop just can't solve.  

Thnx in advance...

Tomas

I had this problem this morning. I set VMware to use NAT for the ethernet and started working. For some reason it wouldn't work in bridged mode. It had all the correct information but wouldn't connect to the internet.

---

### Post by nilfilter on 2006-07-27
My NIC (eth0) is bridged as well and does not suffer from connectivity issues. Did you set the *Connect at power on* option in VM|Settings? Other than that, I wouldn't know where else to look.

---

### Post by BigCdaAnswer3 on 2006-07-27
Bridged vmware connections need a mac address of the form 00:50:56:XX:XX:XX, and you can set this in your virtual machine's .vmx file. you'll need to remove all the lines that start with ethernet0(or whatever interface you'll be using) and replace them with something like this.

ethernet0.addressType = "static"
ethernet0.address = "00:50:56:XX:XX:XX"

---

### Post by st00ner on 2006-07-27
VMware dosnt even work for me at all with -26 kernel. 25 works good though

---

### Post by wanorris on 2006-07-27
I'm having a different networking problem running Dapper inside VMWare under XP. I apologize if I should have started a new thread on this -- I'm new to the forum, and figured I would err on the side of conserving threads. :) 

I've been having this problem both under Breezy and since I upgraded to Dapper.

Anyway, when I'm at home connected through 802.11g to a home router and from there to a cable modem, the internet connection works fine from the Ubuntu virtual machine.

By contrast, when I'm at the office and connected by ethernet to the LAN, DNS doesn't work -- it simply fails to pick up the DNS servers. If I look up the DNS servers that Windows is using and add them manually using the Networking tool in Ubuntu, it starts to work again. But then 5 or 10 minutes later, it will purge those settings and lose DNS again.

To make it easier to patch this, I created an alias in .bashrc for a command to use sudo to replace /etc/resolv.conf with a version that contains the correct settings. This works to patch things easily, but it's obviously a band aid for the problem rather than an actual solution.

Can anyone tell me why this is happening and if there is any solution for it? Internet access isn't my main use for my Ubuntu VM, but as you might imagine, this is rather annoying. Thanks in advance. :)

---

### Post by wanorris on 2006-07-28
bump

---

### Post by lefnire on 2007-10-07
bump

---

### Post by csioucs on 2007-11-13
No. The issue is bugging me. I have internet access only in the VM and in Ubuntu Zero. Even if the VM is shut down. I am surprised that there aren't many answers to this. I am still searching for a solution since only the bridged connection is working. the others shut internet access for all machines, host and guest.

---

