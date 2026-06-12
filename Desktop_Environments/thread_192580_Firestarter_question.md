---
title: "Firestarter question"
date: 2006-06-08
forum: Desktop Environments
---

### Post by DarkStarDeity on 2006-06-08
As I understand it, iptables is the firewall in Ubuntu and is always runnning, Firestarter is just a gui tool to help configure it and it is not actually necessary to have Firestarter running in order to be protected. Is this correct, or do I need to have Firestarter up and running in order for the firewall to be on? If the latter, how can I get Firestarter to run on startup? I forget to start it unless I need to change a rule.

---

### Post by 23meg on 2006-06-08
iptables is the program used to adjust the kernel's IP traffic rules, and Firestarter is a frontend to it, making it easier to adjust the IP traffic rules without knowing anything about iptables.

If you install Firestarter it will always be on at startup by default, even when its GUI isn't displayed. You only need the GUI for viewing incoming / outgoing connections and making changes to your configuration.

---

### Post by DarkStarDeity on 2006-06-08
That's what I thought, thanks for that.

One more question - if I shutdown the firewall with Firestarter, I presume that this would then forward the request and shutdown iptables, leaving my system vulnerable until I started it up again, is this correct?

---

### Post by meng on 2006-06-08
Yes if you stop the firewall you're letting your guard down.

---

### Post by 23meg on 2006-06-08
Not exactly; first of all neither iptables, nor Firestarter are "firewalls" per se. Second, you only really need a firewall kind of protection if you're running software that's listening on certain ports, in other words, if you have open ports. In a default Ubuntu installation there are no open ports, so as long as you don't explicity install something that listens on a particular port (for example SSH), you're not vulnerable to a possible attack or exploit on that port, so you don't need a firewall to protect you from such a possibility.

---

### Post by DarkStarDeity on 2006-06-08
I'm running samba, and Firestarter made sharing the internet connection with another machine so much easier than manually configuring NAT and masquerading (I have a high-level understanding of these things but I'm no admin), so I need it for those things.

---

### Post by 23meg on 2006-06-09
So perhaps it's best for you to keep it running. Remember that it's running on startup and will keep running even when its GUI is shut down. Also see this post:

[http://ubuntuforums.org/showpost.php?p=1111336&postcount=11](http://ubuntuforums.org/showpost.php?p=1111336&postcount=11)

---

