---
title: "apt-get doesn't work :-("
date: 2015-03-19
forum: Desktop Environments
---

### Post by nibal on 2015-03-19
Each time I try to install a new package in my 14.04 Ubuntu x64, I get:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vim-gnome is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```
I end up downloading the package manually from the web site, as well as any dependencies. How can i make apt-get work?

---

### Post by deadflowr on 2015-03-19
What's the output for 
```
sudo apt-get update
```
This is where you can usually see where apt is going bonkers for this particular problem.
I take it the network connection is working, otherwise...

---

### Post by nibal on 2015-03-19
Ty. That did it. Seems after updating apt-get, it works again;-)
 Since you asked for output, here are the first few lines:
```

Ign http://gr.archive.ubuntu.com trusty InRelease
Ign http://gr.archive.ubuntu.com trusty-updates InRelease                      
Ign http://gr.archive.ubuntu.com trusty-backports InRelease                    
Get:1 http://gr.archive.ubuntu.com trusty Release.gpg [933 B]                  
Get:2 http://gr.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Get:3 http://gr.archive.ubuntu.com trusty-backports Release.gpg [933 B]        
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:4 http://gr.archive.ubuntu.com trusty Release [58.5 kB]
.
.
.

```

---

