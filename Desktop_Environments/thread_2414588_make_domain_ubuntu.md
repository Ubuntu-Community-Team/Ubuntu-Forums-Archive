---
title: "make domain ubuntu"
date: 2019-03-12
forum: Desktop Environments
---

### Post by m.eraj1995 on 2019-03-12
Dear Team,

i have one query, suppose i installed ubuntu 
on my all systems of office then can i make 
one machine as a server or domain to control all
my systems as client,
is it possible, because now i am going install
ubuntu on my all office systems so is that possible.

---

### Post by Frogs Hair on 2019-03-12
[This]("https://help.ubuntu.com/lts/serverguide/samba-dc.html.en") would be a starting point there are many articles on the subject so doing some research would be a good idea . 


 [https://wiki.samba.org/index.php/Main_Page](https://wiki.samba.org/index.php/Main_Page)

---

### Post by SeijiSensei on 2019-03-12
If all the machines are running Ubuntu, you want to use NFS not Samba.  But yes, one machine can be a server and store files used by the clients. (It can also function as a mail server, a web proxy, a DNS server, a DHCP server, and many other things at the same time.)

Might I suggest that rather than converting the entire office, you start with just two machines, one as the server as one as the client.  It will take you a while to work out all the bugs.  Once you're done you can consider converting other workstations.

If you have a bunch of machines to manage, you probably need to look into authentication systems.  The hoary NIS is pretty easy to set up; LDAP not so much.

---

### Post by m.eraj1995 on 2019-03-12
ok sir,

---

