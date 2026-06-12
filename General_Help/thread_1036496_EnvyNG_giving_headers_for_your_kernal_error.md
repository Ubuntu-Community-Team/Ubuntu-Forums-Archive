---
title: "EnvyNG giving headers for your kernal error"
date: 2009-01-10
forum: General Help
---

### Post by gamer4lyf3 on 2009-01-10
Hey everyone. recently I guess I updated my Ubuntu with just regular updates. When I booted it back up my graphics were all messed up so I'm using failsafe graphic now. I'm trying to use EnvyNG to install my Nvidia drivers again but when I start it up I get this error "EnvyNG has detected that the headers for your kernel are missing and cannot be installed". Can anyone help me with this? Oh and I'm using Ubuntu 8.10.

---

### Post by mikewhatever on 2009-01-11
Make sure the **linux-headers-generic** package is installed, then run <sudo apt-get update && sudo apt-get upgrade>.

---

