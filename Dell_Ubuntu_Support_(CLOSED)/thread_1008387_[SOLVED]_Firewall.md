---
title: "[SOLVED] Firewall?"
date: 2008-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by saxuntu on 2008-12-11
I got on synamptic to download fire stater to configure my firewall.  After entering the search for "firewall" i was surprised to see iptables was not installed. This surprised me since iptables is the actual firewall in the regular ubuntu distro.  Does Dell have a different one running or did they actually the pull the firewall?  If so how freaking stupid.

---

### Post by saxuntu on 2008-12-11
I went to download firestater for my new mini 9 and noticed iptables was not installed.  Has dell striped the standard firewall?  Did they replace it with something else?

---

### Post by usstitan on 2008-12-11
hi, i have a dell inspiron 1525 with ubuntu pre installed, only had it a few weeks back and i just checked mine for iptables and it is installed. Perhaps dell just made a mistake while doing yours?

---

### Post by notwen on 2008-12-11
> **saxuntu said:**
> I went to download firestater for my new mini 9 and noticed iptables was not installed.  Has dell striped the standard firewall?  Did they replace it with something else?

Did you attempt to install it?  I'm betting this also falls back on them using the lpia kernel over the regular x86 for the Mini's Atom processor.  This is kernel built to take advantage of your Atom processor's power saving capabilities.  Try installing it, I'm betting it won't since you'd need a custom compiled version for your lpia kernel.  

Search this forum for more issues users are having regarding the lipa kernel that Dell shipped w/ the Mini 9s.

---

### Post by Rocket2DMn on 2008-12-11
Merged posts - please don't create multiple threads on the same topic, just reply to your original one.

I don't believe that iptables is installed by default, iptables is actually an interface to Netfilter which talks to the linux kernel about using the network.  iptables doesn't need to be installed for the firewall to work, only to configure it.

---

### Post by notwen on 2008-12-11
> **Rocket2DMn said:**
> Merged posts - please don't create multiple threads on the same topic, just reply to your original one.

I don't believe that iptables is installed by default, iptables is actually an interface to Netfilter which talks to the linux kernel about using the network.  iptables doesn't need to be installed for the firewall to work, only to configure it.

I stand corrected, thanks for the correlation.  =]

---

### Post by saxuntu on 2008-12-11
Thanks for the help.

---

