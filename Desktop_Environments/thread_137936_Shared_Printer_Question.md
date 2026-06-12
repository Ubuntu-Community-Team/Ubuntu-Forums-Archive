---
title: "Shared Printer Question"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Justbill on 2006-02-28
I have an HP 1315 PSC on my computer in another room. I have 2 computers on a WIRED network. The printer is connected to box 1 (Goliath. running FC4). I have, in the past been able to print to the printer at box 1, from box 2, when I had CentOS 4.2 on box 2, with the firewalls enabled on both boxes. I was using SELinux on both (still using SELinux on box 1). I have put Guarddog on box 2, since I have switched to Ubuntu. With Guarddog enabled I can NOT print from box 2, if I dis-able Guarddog, I am able to print. Can someone give me some direction with Guarddog, or if there is a better firewall to use (I am somewhat familiar with SELinux already). I am quite sure this is something simple I am overlooking. I can ping box 1 from box 2, using IP address, or hostname. 

Thanks in advance, for any help
Justbill

Afterthought: Here is how my /etc/hosts file looks

127.0.0.1       localhost.localdomain   localhost      Ulysses.justbillsguitars.com
192.168.2.2     Goliath.justbillsguitars.com   localhost  localhost
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
~


Should "localhost.localdomain"  be switched  with "Ulysses.justbillsguitars.com" ?  The reason I ask, is because when I tried to mount a shared file, I got the response, "Permision Denied". On box 1, the second line in /etc/hosts is:
192.168.2.5    Ulysses.justbillsguitars.com     localhost   localhost

I am using NFS for my file sharing, or I should say that is what I have been using previously, this was the syntax I used 

sudo mount -t nfs Goliath.justbillsguitars.com:/home/Bill /mnt

this has worked for me on the past with CentOS, do I need to do something different in Ubuntu?

Thanks
Justbill

---

