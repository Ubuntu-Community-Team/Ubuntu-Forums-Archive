---
title: "cannot add users and synaptic won't run"
date: 2008-05-02
forum: Desktop Environments
---

### Post by atl_CCk on 2008-05-02
When I try to run synaptic package manager, nothing happens.  When I try to run Users and groups nothing happens.

It does not ask for root or access password.

atl_CCk

---

### Post by p_quarles on 2008-05-02
Apparently there is a common problem with "sudo" in 8.04 that stems from the fact that the hostname is misconfigured. To see if that's the problem, type:
```
cat /etc/hosts
```
The second line should read something like this:
```
127.0.1.1     ubuntu-desktop
```
Now, run this:
```
hostname
```
This will output whatever name you gave the computer during installation. It should match the second column of the output of the previous command. If it doesn't, there's your problem. 

If they do match, already, try running another root operation, e.g.:
```
sudo apt-get update
```
and report any error messages you receive.

---

