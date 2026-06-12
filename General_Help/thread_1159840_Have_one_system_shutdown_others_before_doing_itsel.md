---
title: "Have one system shutdown others before doing itself"
date: 2009-05-15
forum: General Help
---

### Post by joebert on 2009-05-15
My situation is that I have multiple (fairly close to stock) Ubuntu systems on a small network, one has a monitor connected and the others do not.

What I would like to do is, when I shutdown the system with a monitor attached, it should go through and shutdown every other system on the network. I'd like to skip this behavior during reboots however.

Normally what I do is go through SSH into each system and issue a shutdown command.

```
sudo shutdown -h 0
```

Problem is unless I want to fiddle around with /etc/sudoers and let the administrator group issue sudo commands without passwords, I'm not sure how I can shutdown the remote systems automatically.

---

### Post by dcstar on 2009-05-15
> **joebert said:**
> My situation is that I have multiple (fairly close to stock) Ubuntu systems on a small network, one has a monitor connected and the others do not.

What I would like to do is, when I shutdown the system with a monitor attached, it should go through and shutdown every other system on the network. I'd like to skip this behavior during reboots however.

Normally what I do is go through SSH into each system and issue a shutdown command.

```
sudo shutdown -h 0
```

Problem is unless I want to fiddle around with /etc/sudoers and let the administrator group issue sudo commands without passwords, I'm not sure how I can shutdown the remote systems automatically.

Personally I would simply use SSH to log into the machines using the root account with the command and credentials on one command line, but since enabling the root account on Ubuntu is "taboo" in these forums I guess you are just going to have to live with the things the way they are....

---

