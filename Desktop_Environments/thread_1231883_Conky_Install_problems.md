---
title: "Conky Install problems"
date: 2009-08-05
forum: Desktop Environments
---

### Post by epic concept on 2009-08-05
I've been trying to install Conky for some time now but it keeps giving me the same error

I type 
sudo apt-get --assume-yes install conky
in the terminal and I get the following message.


E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any Ideas?

---

### Post by SoftwareExplorer on 2009-08-05
Does any user have synaptic, Add/Remove programs, apt-get, or dpkg running?

dpkg is terminal based by the way.

Another option is that one of the aforementioned programs got forcefully closed.

---

