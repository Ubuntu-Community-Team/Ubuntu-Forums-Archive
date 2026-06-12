---
title: "cairo-clock, with beryl already installed"
date: 2007-02-20
forum: Desktop Environments
---

### Post by kpkeerthi on 2007-02-20
I already have beryl installed and working. Here is what aptitude is trying to do when I choose to install cairo-clock. Should I proceed? Is it OK to have compiz and beryl coexist?
 
```

~$ sudo aptitude install cairo-clock 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  compiz compiz-core compiz-gnome compiz-plugins xcompmgr 
The following NEW packages will be installed:
  cairo-clock compiz compiz-core compiz-gnome compiz-plugins xcompmgr 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 780kB of archives. After unpacking 5157kB will be used.
Do you want to continue? [Y/n/?] 

```

---

### Post by Jeremy23 on 2007-02-21
That should be fine. They can perfectly well coexist together, although they can't run at the same time.

However, cairo-clock shouldn't be depending on those packages, as, like you're doing, when you run Beryl you don't need Compiz installed. They should be *suggested*, not *depended on*.

---

