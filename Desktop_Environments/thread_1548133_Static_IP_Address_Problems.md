---
title: "Static IP Address Problems"
date: 2010-08-07
forum: Desktop Environments
---

### Post by racertim on 2010-08-07
I've seen a ton of posts about this and researched it, but I just can't seem to get this working.

Background: 
I'm trying to setup a machine using 10.04 desktop to use as a home server. I want to store files and use it for PHP development. When I have it setup, I want to keep it in the basement only connected to the router, no monitor, etc and just administer it via VNC from my primary Windows 7 machine.

Problem:
This appears to be the simplest set of instructions for setting up a static IP address:

[http://www.liberiangeek.net/2010/06/how-to-configure-static-ip-addresses-in-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/06/how-to-configure-static-ip-addresses-in-ubuntu-10-04-lucid-lynx/)

When I follow these instructions, I can use SSH to get to the machine, but it doesn't have internet access. Then if I switch back to DHCP I have internet access but I can't access the machine with SSH.

What do I need to do to get both to work? Also, once I get this figured out, installing VNC should be pretty easy right?

---

### Post by racertim on 2010-08-07
[http://ubuntuforums.org/showthread.php?t=1545878](http://ubuntuforums.org/showthread.php?t=1545878)

This post was helpful. The main difference was including 192.168.1.1 as my DNS. It seems to work now, but the internet connection is super slow. It takes forever to get a page to come up. Is there a better way to set this up?

---

### Post by spyrule on 2010-08-07
I could be wrong, but I think you'd need to set up a static IP through your router, or whatever is serving your DHCP. 

As far as it taking a long time for you to browse the internet with the IP of 192.168.1.1; 192.168.1.1 is an internal address and unless it is the address to your DNS server what's probably happening is that your computer first tries to connect to 192.168.1.1 and when it doesn't find any info it eventually times out and then finds your isp's DNS server.

---

### Post by Bachstelze on 2010-08-07
> **racertim said:**
> [http://ubuntuforums.org/showthread.php?t=1545878](http://ubuntuforums.org/showthread.php?t=1545878)

This post was helpful. The main difference was including 192.168.1.1 as my DNS. It seems to work now, but the internet connection is super slow. It takes forever to get a page to come up. Is there a better way to set this up?

Find out which DNS servers your machine uses when configured with DHCP (in /etc/resolv.conf), and configure it to use that when using a static IP.

---

### Post by racertim on 2010-08-08
That took care of it, just as fast as the DHCP settings now. Thank you!

---

