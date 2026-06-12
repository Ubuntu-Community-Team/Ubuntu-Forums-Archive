---
title: "Synaptic Update Failure"
date: 2009-04-15
forum: General Help
---

### Post by xr4v3nx on 2009-04-15
Hello guys..after I installed Amarok and enabled MP3s, I tried to open the Synaptic Package Manager (Add/Remove Programs). And a window poped out with this:

**Failed to check for installed and available applications**

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

How can I fix this guys?

---

### Post by taurus on 2009-04-15
Make sure you close synaptic first.  Then, open a terminal and run those two commands, one at a time.

```
sudo apt-get install -f
sudo apt-get update
```
Any error messages?

---

