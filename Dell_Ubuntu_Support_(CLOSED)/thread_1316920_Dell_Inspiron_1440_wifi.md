---
title: "Dell Inspiron 1440 wifi"
date: 2009-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tapas_mishra on 2009-11-06
I want to know which are the important files for bringing my wifi card up again if I uninstall gnome network manager due to some reason.I want to re install the wifi driver on the Dell Inspiron 1440 how can this be done.

---

### Post by purplewakanda on 2009-11-06
Open up a terminal and type "sudo apt-get install wifi-radar", without quotes.

---

### Post by tapas_mishra on 2009-11-06
what is this package wifi radar for

---

### Post by tapas_mishra on 2009-11-08
> **tapas_mishra said:**
> I want to know which are the important files for bringing my wifi card up again if I uninstall gnome network manager due to some reason.I want to re install the wifi driver on the Dell Inspiron 1440 how can this be done.
I think I have found a solution I had been browsing the repositories here
[http://packages.ubuntu.com/jaunty/net/network-manager-gnome](http://packages.ubuntu.com/jaunty/net/network-manager-gnome)
but still what other files are needed that is not clear to me.Any help would be appreciated.

---

### Post by tapas_mishra on 2009-11-12
I have finally got some luck in trying over Xen there are supported Operating System and some Operating Systems do not support 
I had been googling since I was getting a lot of errors as I had tried to install Xen or say compile a Dom0 kernel on it from jeremy repository on the unsupported OS,
and since from my post it is absolutely clear that I am a novice as far as Xen is concerned 
I came across a good book about XEN 
A hands on guide to the art of virtualization Jeanna Mathews
[http://www.amazon.ca/Running-Xen-Hands-Guide-Virtualization/dp/0132349663/ref=sr_1_3/189-9122115-5316947?ie=UTF8&s=books&qid=1258034980&sr=1-3](http://www.amazon.ca/Running-Xen-Hands-Guide-Virtualization/dp/0132349663/ref=sr_1_3/189-9122115-5316947?ie=UTF8&s=books&qid=1258034980&sr=1-3)

I am posting the above link so that if some one like me is searching for a lot of basic questions among documentations etc does not get confused by the blogs on internet everything available for free does not leads to the right solution.But still it has a lot of support on the community and a good place to ask questionbs is [http://gmane.org]("http://gmane.org/") the mailing list about xen users it is here 
[http://lists.xensource.com/xen-users](http://lists.xensource.com/xen-users)

A relevant thing to search on internet will be 
CONFIG_XEN_PCI
CONFIG_NETXEN_NIC
Initially they appear to be jargons but if you keep googling and reading you will reach answers.

---

