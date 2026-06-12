---
title: "dhcp at startup not working"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Eremit on 2005-10-25
my /etc/network/interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

But after booting I have to do "/etc/init.d/networking restart" to get an IP

It worked before the upgrade to Breezy (from Hoary).
Any ideas?

---

### Post by mlomker on 2005-10-25
I don't have a direct solution, but [installing ifplugd]("http://www.ubuntuforums.org/showthread.php?p=394505#post394505") might be a good work-around.

---

### Post by ecobuntu on 2005-10-25
[QUOTE=Eremit]my /etc/network/interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

But after booting I have to do "/etc/init.d/networking restart" to get an IP

It worked before the upgrade to Breezy (from Hoary).
Any ideas?[/QUOTE]


If you're using a laptop i recommend grabbing the laptop-net package.  
sudo apt-get install laptop-net
It automatically does you DHCP and it's great for laptops.  Works like a charm here!

---

### Post by Eremit on 2005-10-27
thanks for your replies, maybe I give ifplugd a try.
I'm not a laptop user.
I think it's the same bug as filed here:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15340](http://bugzilla.ubuntu.com/show_bug.cgi?id=15340)

---

