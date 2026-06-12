---
title: "Evolution with exchange-connector really slow in jaunty"
date: 2009-05-01
forum: General Help
---

### Post by gen.alcazar on 2009-05-01
Hi Everyone:

I recently did a double upgrade, going from Hardy to Intrepid to Jaunty, and noticed that evolution is really slow when scanning for changed messages and downloading mail for offline viewing.  I'm using Evolution 2.26.1, with evolution-exchange 2.26.0, and check mail off of an Exchange 2003 server (I think).  This was pretty zippy in hardy, but with Jaunty, it takes about 15 minutes for Evolution to get done scanning for new mail in all folders.

I noticed a couple of bugs filed for this:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/evolution-exchange/+bug/292739](https://bugs.launchpad.net/ubuntu/jaunty/+source/evolution-exchange/+bug/292739)

and in upstream:
[http://bugzilla.gnome.org/show_bug.cgi?id=558883](http://bugzilla.gnome.org/show_bug.cgi?id=558883)

But they both seem to be fixed.  I'm a little confused as to whether my versions have the fix or not.  If they don't, then any ideas on how to figure out when the next set of updates is coming through?  If yes, then any other suggestions will be greatly appreciated.  I've already disabled IPv6, but no improvement.

Thanks!

---

### Post by pwebster25 on 2009-05-07
I also have an extremely slow experience when I upgraded from Intrepid to Jaunty.  Evolution freezes up and turns grey for a couple minutes while it seems to think.  My system monitor shows that 100% of the cpu is being used.  I connect to an exchange server on an MS network with AD connection via likewiseopen. None of the bug reports mentioned above offered me any safe solutions (based on my expertise level).

I am going to try evolution-exchange-dbg.  We'll see.

---

### Post by briansrapier on 2009-05-11
How did you disable IPV6? In previous editions, IPV6 was a module, but in Jaunty, it is built into the kernel. The only way to disable it is to rebuild the kernel.

See this thread for details:
[http://ubuntuforums.org/showthread.php?t=1065469](http://ubuntuforums.org/showthread.php?t=1065469)

I'm having similar problems. It appears to be an upstream kernel issue:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/365588](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/365588)

---

### Post by briansrapier on 2009-05-11
Here is what worked for me:

Temp fix:
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6

More permanent workaround:
# vi /etc/sysctl.conf

add:

net.ipv6.conf.all.disable_ipv6 = 1

My performance for Evolution appears to be back to normal.

---

### Post by jwkaisd on 2010-04-26
I tried the:
# vi /etc/sysctl.conf and add: net.ipv6.conf.all.disable_ipv6 = 1

My performance was unchanged.  I had to do sudo to edit the file.

My performance for Evolution appears to be back to normal. 	

I also tried the echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6 to no avail.  Actually, it complained that I didn't have permission even when preceding it with sudo.

The upgrade from hardy to jaunty is fabulous (with Evolution being the single dissapointment).

On Hardy, evolution was very buggy and froze often, but it was not slow to update new email.

Any suggestions will be greatly appreciated!  Cheers!

---

### Post by jwkaisd on 2010-04-26
I followed the bug report suggested, and saw that there are some more instances of ipv6.  I disabled them all, and the problem seems much improved!

Thanks!!!  John:)

---

