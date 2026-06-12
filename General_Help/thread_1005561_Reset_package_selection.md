---
title: "Reset package selection"
date: 2008-12-08
forum: General Help
---

### Post by .nedberg on 2008-12-08
Hi

I have a Kubuntu (and Xubuntu and Ubuntu for that matter) virtual machine. I would like to "reset" the package selection to the way it was right after installation. All the packages I have installed since then need to go, excluding updates.

I did some searching and could not find a way to do this. All I could find was
```

dpkg --get-selections

```
But that also lists default programs. If someone could provide a way to restore the default selection I would be happy. If you have a standard K/X/Ubuntu VM, could you run the command and attach the output I think I could run a diff on the two lists and hopefully restore my VM to default.

---

