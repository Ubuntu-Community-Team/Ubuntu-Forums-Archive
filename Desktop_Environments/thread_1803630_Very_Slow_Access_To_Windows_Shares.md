---
title: "Very Slow Access To Windows Shares"
date: 2011-07-13
forum: Desktop Environments
---

### Post by Maeglin on 2011-07-13
Hello Ubuntu Community!

My first post, having only installed 11.04 at the weekend on one of my old PCs.

Everything is up & running pretty well, I have a 100BT home network with 4 Windows XP PCs and a Synology DS211j server.

I can see & access these other shares from Ubuntu, but it's so slow to connect, approx. 45 seconds each time, compared to almost instant from any of the XP machines.

Could someone suggest how this performance could be improved?

Many thanks.

---

### Post by maestrobwh1 on 2011-07-13
I have had similar issues.  Add the IP address for your share in /etc/hosts in a new line right under the line that lists your guest,  No need to reboot; it should just work.

192.168.15.100 is the IP for my host shares, and the name of the machine is EEE-BOX

Mine looks like this:
192.168.15.101  ubuntu-1201T    # Added by NetworkManager
127.0.0.1       localhost.localdomain   localhost
::1     ubuntu-1201T    localhost6.localdomain6 localhost6
127.0.1.1       ubuntu-1201T
**192.168.15.100  EEE-BOX**
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Maeglin on 2011-07-14
Hi maestrobwh1 & thanks!

That seems to have done the trick.

I didn't use the terminal to edit the hosts file, (that's a part of Ubuntu I don't like), but I found the gnome-network-admin GUI which was really easy to add the required ip addresses.

Thanks again.

---

