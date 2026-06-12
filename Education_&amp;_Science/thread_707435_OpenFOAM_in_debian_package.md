---
title: "OpenFOAM in debian package"
date: 2008-02-25
forum: Education &amp; Science
---

### Post by jlawrence on 2008-02-25
Hi,

I was looking for an easy way to install OpenFOAM in Ubuntu and came across this page.

I am aware of the instruction on how to install OpenFOAM in Ubuntu as a forum thread and wiki page, but still it sounds very complicated to a newbie like me.

I am not sure what will be the appropriate way to make deb package for OpenFOAM, but is it possible to just use the rpm package from this webpage ?
[http://www.rage.net/aero/](http://www.rage.net/aero/)

This method may become an alternative way to install OpenFOAM.

I think the Ubuntu Science community can get lots of benefit it this software is available via "apt-get install" as well.

Regards,

---

### Post by thisismalhotra on 2008-02-25
> **jlawrence said:**
> Hi,

I was looking for an easy way to install OpenFOAM in Ubuntu and came across this page.

I am aware of the instruction on how to install OpenFOAM in Ubuntu as a forum thread and wiki page, but still it sounds very complicated to a newbie like me.

I am not sure what will be the appropriate way to make deb package for OpenFOAM, but is it possible to just use the rpm package from this webpage ?
[http://www.rage.net/aero/](http://www.rage.net/aero/)

This method may become an alternative way to install OpenFOAM.

I think the Ubuntu Science community can get lots of benefit it this software is available via "apt-get install" as well.

Regards,

Yes using a pckage called alien you can easily convert a .rpm to a.deb package. Here this link will help a lot...

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Also, if you make a .deb you can save it a send it for other users to use and install. One more things you can request developers (just don't remember now where) and offer your deb to be included in repos by default... This will be a good time to do it as they are revamping the repos for next release.

---

### Post by jlawrence on 2008-02-27
thisismalthora,

unfortunately the rpm package is one version older than the newest one.
I installed it according to the method written in this forum.

I was lucky that I did not have any problems during installation. (according to the manual I had to ignore some fatal error messages, which made me nervous).

It will be good if someone can come with deb package to ease installation and uninstallation of this program.

Thank you,

---

### Post by thisismalhotra on 2008-03-04
> **jlawrence said:**
> thisismalthora,

unfortunately the rpm package is one version older than the newest one.
I installed it according to the method written in this forum.

I was lucky that I did not have any problems during installation. (according to the manual I had to ignore some fatal error messages, which made me nervous).

It will be good if someone can come with deb package to ease installation and uninstallation of this program.

Thank you,

Can we get the source of it.. I can give it a try??:confused:

---

