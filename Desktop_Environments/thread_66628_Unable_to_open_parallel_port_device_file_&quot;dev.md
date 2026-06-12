---
title: "Unable to open parallel port device file &quot;/dev/lp0&quot;: Permission denied"
date: 2005-09-17
forum: Desktop Environments
---

### Post by perlmonger on 2005-09-17
"Unable to open parallel port device file "/dev/lp0": Permission denied"

I can't get a printer to work and I think this is the problem. I've googled it and searched the forums here but can't find a solution. I did find a thread here by someone with the same problem but he never got an answer. Has anyone found a solution to this or does anyone know what it means exactly?  :-x

---

### Post by cwaldbieser on 2005-09-18
[QUOTE=perlmonger]"Unable to open parallel port device file "/dev/lp0": Permission denied"

I can't get a printer to work and I think this is the problem. I've googled it and searched the forums here but can't find a solution. I did find a thread here by someone with the same problem but he never got an answer. Has anyone found a solution to this or does anyone know what it means exactly?  :-x[/QUOTE]

Well, /dev/lp0 is the parellel printer port.  If you type:
```
$ ls -l /dev/lp0
``` 
what are the permissions that are set on it?  Try sudo chmod-ing it to 777 (all permissions for everyone) and see if that helps.

---

