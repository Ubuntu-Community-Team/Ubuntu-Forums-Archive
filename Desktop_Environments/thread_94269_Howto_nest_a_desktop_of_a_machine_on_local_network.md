---
title: "Howto nest a desktop of a machine on local network"
date: 2005-11-23
forum: Desktop Environments
---

### Post by davro on 2005-11-23
Hi all

Hope that the title is not to confusing.

nutshell
Basically what i would like is to get a login screen of a remote machine.
I have another ubuntu machine on my network and i would simply like 
to have a command that i can run so i can have a nested session.
but preferably not using vnc
/nutshell

This is sort of what i would like but on the remote machine
```
gdmflexiserver --xnest
```

Something like this
```
gdmflexiserver --xnest 192.168.0.99
```

any help would be gratefully received.

---

### Post by ElijahLofgren on 2005-12-17
The following command should do what you want. It works for me. ;) 

```
Xnest :2 -query 192.168.0.99
```

---

