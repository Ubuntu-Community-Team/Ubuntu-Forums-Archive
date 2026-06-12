---
title: "hosts file keeps reverting"
date: 2011-08-03
forum: Desktop Environments
---

### Post by WarSpanner on 2011-08-03
Hello,

I'm configuring Apache to work from several development directories as per these instructions: [http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/](http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/)

Got it all to work ok, for a while but then when I reboot the entries I've made in the hosts file dissapear and I can no longer use them.

I'm assuming DHCP reverts the hosts file or something?

What's the 'proper' way to get an entry into a hosts file and have it stay there?

Thanks in advance.

---

### Post by sillyxone on 2011-08-03
I just upgraded from 10.04 to 10.10 (a new work laptop) and couldn't retain the local alias for Apache after reboot too.

There seems to be a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/659872](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/659872)

---

### Post by WarSpanner on 2011-08-03
Oh poo...

and response 'why bother fixing it' doesn't sound very hopeful either.... :(

I guess this is why people tell me they always switch to other distros for hosting.

---

### Post by WarSpanner on 2011-08-03
Just a thought...

If I deny write access for everyone to the file, wouldn't that stop the network manager overwriting the file?
;-)

/Re-EDIT:
Aha...
sudo chattr +i /etc/hosts
take that Network Manager! :p

---

