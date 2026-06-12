---
title: "persisting sysctl -w"
date: 2009-01-03
forum: General Help
---

### Post by djshaw on 2009-01-03
I'm trying to run mit-scheme. Whenever I run scheme I get the error

> 
$ scheme
Largest address does not fit in datum field of object.
Allocate less space or re-configure without HEAP_IN_LOW_MEMORY.


The work around is 

> 
sudo sysctl -w vm.mmap_min_addr=0


Because I don't want to run sysctl every time I boot up my box, I put

> 
vm.mmap_min_addr=0


in my /etc/sysctl.conf file. However, when I boot up, scheme give me HEAP_IN_LOW_MEMORY error. It is apparent that I have not put the entry in the /etc/sysctl.conf file correctly. Does anyone know what the correct entry should be?

-Thanks



my fill sysctl.conf file:

> 
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167)),
# and is not recommended.
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
# The contents of /proc/<pid>/maps and smaps files are only visible to
# readers that are allowed to ptrace() the process
# sys.kernel.maps_protect = 1

vm.mmap_min_addr=0



---

### Post by sdennie on 2009-01-03
I believe sysctl runs very early in the boot process so it's possible that something later in the boot process is overriding your value.  Does it work if you put your literal workaround (sysctl -w ...) in /etc/rc.local?  That gets executed very late in the boot process.

---

### Post by adriant42 on 2009-01-04
I have a similar problem with timing on when sysctl.conf gets loaded up.

See my thread on [http://ubuntuforums.org/showthread.php?t=1030515](http://ubuntuforums.org/showthread.php?t=1030515) for a possible solution. Of course you may need to adjust the command line to your need. The point is that using the sleep command could delay the loading process until everything else is completed.

Hope this helps

---

