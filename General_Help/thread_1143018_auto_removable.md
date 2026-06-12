---
title: "auto removable"
date: 2009-04-29
forum: General Help
---

### Post by Irony on 2009-04-29
Is there a command to assign *Installed (auto removable)* packages in synaptic to *Installed*.

i.e. a command something like *aptitude keep-all* but in apt form?

---

### Post by Irony on 2009-04-30
Well, I decided to run the command;

```
# aptitude keep-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Reading task descriptions... Done         
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Reading task descriptions... Done
```

And much to my surprise it moved *auto removable* into the *installed* status just as I wanted.

I was assuming this would not work because I thought that synaptic was a gui front end for *apt* but it seems that *aptitude* affects synaptic as well.

---

