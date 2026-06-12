---
title: "How do I remove/uninstall the vmware player?"
date: 2006-02-27
forum: Desktop Environments
---

### Post by somas1 on 2006-02-27
I installed vmware player using the instructions from an ubuntu wiki.  The player works well but now that vmware server is free I'd like to check it out but can't until I uninstall vmware player.  Since I installed vmware player using make and not apt, I don't know how to uninstall it.  

Can any give me any pointers on this?

---

### Post by Swiss on 2006-02-27
Try going into Synaptic and searching for the program, and if checked, uncheck and click apply.

---

### Post by somas1 on 2006-02-27
[QUOTE=Swiss]Try going into Synaptic and searching for the program, and if checked, uncheck and click apply.[/QUOTE]


thanks, I'll try that.  I thought tools like Synaptic were not an option when you build from source.

---

### Post by Swiss on 2006-02-27
I don't know... No harm in trying... ;) 
Before you install something check to see if its in Synaptic first, SYN contains over 16,000 programs so...

---

### Post by Qrk on 2006-02-28
To install vmware you just need to run the install script again.

So if you still have the tar file you downloaded, go to the directory you extracted it and run:

```
sudo ./vmware-install.pl
```

The installer will uninstall it, then ask you if you want to reinstall it.

Or, if you don't have that directory, go to /usr/bin and run:

```
./vmware-uninstall.pl
```

---

### Post by engineering.concepts on 2006-04-17
Thanks Qrk - That worked great!

---

