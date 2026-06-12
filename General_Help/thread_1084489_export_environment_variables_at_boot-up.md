---
title: "export environment variables at boot-up"
date: 2009-03-02
forum: General Help
---

### Post by shan23 on 2009-03-02
Hi,

I'm installing a particular CAD tool which requires a environment variable to be defined as soon as the machine is turned on . I know i could do so by adding a "export ..." line in the .bashrc file, but then ( as far as i know) i have to edit the .bashrc file for all existing users in the machine...Also, i would have to manually add the line to all new users of the system.

I have tried adding the "export ABC=..." line in /etc/rc.d/rc.local , but when i rebooted the machine and logged in from a random account, i found ( by invoking "env" ) that the variable is not defined....

Pls suggest a suitable solution.

---

