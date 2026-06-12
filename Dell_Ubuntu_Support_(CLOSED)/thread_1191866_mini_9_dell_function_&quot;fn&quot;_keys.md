---
title: "mini 9 dell function &quot;fn&quot; keys"
date: 2009-06-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rajanm1 on 2009-06-19
i have a dell mini 9 and updated the software, now when i now click "fn" and "2" it asks me to type my password and then does pretty much nothing useful (it asks me for my wi-fi password). how can i set it back to switching the wi-fi & bluetooth on/off?
also how can i get ubuntu to stop asking me for my password every time i want to change something or have "administrator rights"

thanks

---

### Post by ugm6hr on 2009-06-19
Password entry for Administrator rights is a default security feature in Ubuntu.  You cannot turn it off; it is sensible for any networked computer.

Not sure about the wifi.  Did you update from within Ubuntu, or install the 9.04 version directly?

---

### Post by rajanm1 on 2009-06-19
> **ugm6hr said:**
> Password entry for Administrator rights is a default security feature in Ubuntu.  You cannot turn it off; it is sensible for any networked computer.

Not sure about the wifi.  Did you update from within Ubuntu, or install the 9.04 version directly?

i thought ubuntu was pretty safe anyway and i'm the only one that would use this and it is not my main pc either. but yeh ubuntu came preinstalled and it worked, then i updated it with ubantu and then it didn't work properly. (i'm only on version 8.04 lts)

---

### Post by ugm6hr on 2009-06-20
> **rajanm1 said:**
> i thought ubuntu was pretty safe anyway  

Partly because of its security model: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Can't help with the wifi control; I don't use it, and am now on 9.04.  You can use System -> Prefs -> Airplane Mode to activate airplane mode (and turn off wifi).  I am sure you could reset a keyboard shortcut for it manually, but can't remember how at the moment.

---

### Post by rajanm1 on 2009-06-23
bump, anyone with a dell mini 9 know?

---

### Post by Brandon Williams on 2009-06-23
Dell pushed a new version of network-manager (0.7.0) that partially broke their aircraft-manager utility. It will still turn off your wireless radios, but it will no longer notify network-manager that the wireless network has been disabled. If aircraft-manager doesn't tell network-manager to disable the wireless, then network-manager will never stop trying to reconnect after you disable the radios.

You can find a fixed version of aircraft-manager in [my ppa](https://launchpad.net/~opensource-subakutty/+archive/ppa). I haven't been able to get a response from the upstream maintainer when I've tried to get my changes into the standard version in the Dell repo.

As for asking for an administrator password, you can modify your /etc/sudoers file so that the sudo command does not require password entry. Look for NOPASSWD in 'man sudoers' to figure out the syntax.

---

