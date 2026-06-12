---
title: "Hyperworks for RH 8"
date: 2006-08-30
forum: Desktop Environments
---

### Post by DAharon on 2006-08-30
Hey guys, I'm currently trying to install Hyperworks for RedHat 8 on a laptop running Ubuntu for a professor here at the university.  All the components of the software seem to run fine except for two: HyperView and MotionView.  

When I try to start these up I get an error saying:
Unable to resolve function glXQueryExtension

I'm not so sure where to start searching for the problem, since the other apps in the package use opengl and work fine.

Any pointers would be appreciated.

---

### Post by Parasitor on 2008-07-20
> **DAharon said:**
>  HyperView and MotionView.  

Unable to resolve function glXQueryExtension.

You have to install 3D Direct Rendering with last drivers from ati|nvidia website. Then it works.

---

