---
title: "possible network settings causing problems?"
date: 2005-07-13
forum: Desktop Environments
---

### Post by indygreen on 2005-07-13
hello all,

i have the latest releast of ubuntu installed on my T30 laptop.  when i attempt to send data to the internet while connected to our work network, it will time out.  for example, when i attempt to update my journal, it will time out.  if i do the exact same thing on my desktop machine running fedora core 4, it works fine.  now, if i do this on my network at home, it works fine.  i've checked all of the network settings and they seem to match my desktop machine.  is there something else that i should check. 

thanks for the help.

---

### Post by dataw0lf on 2005-07-13
The settings on the box being the same as your desktop is the exact problem.  Speak with your network administrator and find these out:

What your gateway ip is.
What your netmask is.
If you're using static ips, what ip should you assign to your box.
If you're using dynamic ips, what's the dhcp server.

---

### Post by Arthemys on 2005-07-13
Sounds like it might be an issue with your DNS settings. When you're at work, does a server hand out IP addresses?

**Here's a few threads that may help:**
[http://ubuntuforums.org/showthread.php?t=41103](http://ubuntuforums.org/showthread.php?t=41103)

[http://ubuntuforums.org/showthread.php?t=44813](http://ubuntuforums.org/showthread.php?t=44813)

---

### Post by indygreen on 2005-07-13
[QUOTE=Arthemys]Sounds like it might be an issue with your DNS settings. When you're at work, does a server hand out IP addresses?

**Here's a few threads that may help:**
[http://ubuntuforums.org/showthread.php?t=41103](http://ubuntuforums.org/showthread.php?t=41103)

[http://ubuntuforums.org/showthread.php?t=44813](http://ubuntuforums.org/showthread.php?t=44813)[/QUOTE]

yes.  we're using dynamic here at work.  

thanks for the links.

---

