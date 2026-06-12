---
title: "Ones again... No Network after suspend to ram."
date: 2005-12-16
forum: General Help
---

### Post by gogi on 2005-12-16
Hi all.

I'm new to Ubuntu as I used Debian in the past. My Ubuntuinstallation (5.10) is good. Even suspend to ram works without problems but one. I have no network (adsl connection) after coming back from suspend to ram. I searched the web and found this [site]("http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1923").

After reading I changed my /etc/network/interfaces to this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto dsl-provider
iface dsl-provider inet ppp
        provider dsl-provider
        pre-up /sbin/ifconfig eth0 up

```
But still no success.

After that I entered three commands to get the networking running.
```

sudo /etc/init.d/networking restart
ifup -a
pon dsl-provider

```
And now the network is working. But I don't like to enter these commands after every suspend to ram and so i edited /etc/acpi/resume.sh and replaced at line 57 ifup -a with (/etc/init.d/networking restart && ifup -a && pon dsl-provider) &.

So far so good. But after a new suspend to ram my network still does not work. /var/log/acpid shows these lines.
```

 * Reconfiguring network interfaces...                    [ ok ]
ifup: interface lo already configured
ifup: interface eth0 already configured
ifup: interface dsl-provider already configured
Plugin rp-pppoe.so loaded.

```
The same lines as if i enter the commands manually. But if manually entered the network is running. What's the difference?

I found a line in var/log/acpid which repeats eleven times.
```

Warning: Interface name is `eth0' at line 2, can't be mapped reliably.

```
What could that mean?

Can somebody help?

---

