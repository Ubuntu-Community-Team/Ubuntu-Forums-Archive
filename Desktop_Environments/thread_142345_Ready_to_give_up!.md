---
title: "Ready to give up!"
date: 2006-03-10
forum: Desktop Environments
---

### Post by bugmenot on 2006-03-10
I seriously am about to give up and i have never been a quiter. I am also really trying to get into linux and learn to use it.
My problem is that anything regarding the net will not work. Only ffox, which only works because i disable ipv6 doing the whole changing the aliases file in etc/modprobe.d/aliases
Still Gaim times out, when i try to add an application it simply gets to "downloading file 5 of 7" and hangs as it can't connect to any of these [http://au.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)
[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)
then it gives me all these errors "W: Couldn't stat source package list..."

Any reason why i can recieve email browse the net even ssh, yet these programs do not work? any help appreciated
Thank you in advance

---

### Post by dermotti on 2006-03-10
Do you have a firewall somewhere blocking ports?

---

### Post by bugmenot on 2006-03-10
Nope nothing, just a plain old just installed Ubuntu

---

### Post by missmoondog on 2006-03-10
it has to be something simple. ubuntu is the best at detecting network connections of any linux distro i've tried. in fact, it's been the only distro to get it right, out of the box.

---

### Post by bugmenot on 2006-03-10
I just can't understand why it cannot connect to these servers, when the internet connection is clearly working.
I guess im back to windows or to another distro

---

### Post by kaamos on 2006-03-10
Try hit reload in synaptic and see if that helps, or try removing the "au." from the sources... How are you connected to the net? DSL + router? Something else?

---

### Post by bugmenot on 2006-03-10
i have tried reload, and have the same problem in "update manager".
and yes i am dsl modem router straight to my comp

---

### Post by Aine on 2006-03-10
What's in your /etc/network/interfaces file?

---

### Post by rudiz on 2006-03-10
...

---

### Post by bugmenot on 2006-03-10
Sorry bout that here is my interfaces file 

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
address 10.1.1.3
netmask 255.0.0.0
gateway 10.1.1.1

auto eth0


---

