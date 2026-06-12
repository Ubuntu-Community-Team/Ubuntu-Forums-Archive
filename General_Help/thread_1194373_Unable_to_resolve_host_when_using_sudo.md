---
title: "Unable to resolve host when using sudo"
date: 2009-06-22
forum: General Help
---

### Post by Euphorion on 2009-06-22
Hallo

Since I upgraded to Jaunty, when using sudo I get the message:

sudo: unable to resolve host peter-laptop

The file /etc/hosts contains the following.

127.0.0.1 localhost
127.0.1.1 peter-laptop.HOYLAND

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Question must I edit hosts and remove the .HOYLAND in order to get rid of this nag, or must something else have to be done.

I have search in System->Administration and have not been able to fine an application which allows me to change the host (computer name), does such and application exist?

Thanks in advance

---

### Post by fooman on 2009-06-22
open a terminal and type or copy/paste the following:

```
gksu gedit /etc/hosts
```

when it opens,  edit it so that it looks like this (remove the .HOYLAND from the second line):
```

127.0.0.1 localhost
127.0.1.1 peter-laptop
```

then save and close the file.

hope that helps.

---

### Post by Euphorion on 2009-06-22
Hallo fooman

Have just tried it out and it worked a treat, all back to normal. Thanks for the confirmation of my hunch, have once again learned more about Linux.

---

### Post by jonobr on 2009-06-22
Stupid question,

was why HOYLAND  there in the first place?
If it was there for a reason you could have  the following in /etc/hosts


127.0.1.1 peter-laptop.HOYLAND peter-laptop

This would mean both 
peter-laptop.HOYLAND and
peter-laptop would resolve.

Im thinking removing HORLAND may ciase something to stop working that required that name???

---

