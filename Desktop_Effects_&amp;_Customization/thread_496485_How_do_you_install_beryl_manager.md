---
title: "How do you install beryl manager?"
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by gidra on 2007-07-09
I have beryl on feisty but can't configure it. Some howto please?

---

### Post by Rhubarb on 2007-07-09
```
sudo aptitude install beryl-manager
```

---

### Post by gidra on 2007-07-09
eman@ANTARES:~$ sudo aptitude install beryl-manager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "beryl-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by gidra on 2007-07-09
now what?

---

### Post by shafin on 2007-07-09
> **gidra said:**
> eman@ANTARES:~$ sudo aptitude install beryl-manager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "beryl-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Have you searched synaptic for beryl manager?

---

### Post by gidra on 2007-07-09
yes but it ain't giving any result

---

### Post by hyperair on 2007-07-09
Go to System->Administration->Software Sources and make sure your universe repository is enabled.

---

