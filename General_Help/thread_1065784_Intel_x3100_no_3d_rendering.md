---
title: "Intel x3100 no 3d rendering"
date: 2009-02-10
forum: General Help
---

### Post by xtracool_protik on 2009-02-10
Hi guys,
 my compiz was working exactly fine(well expect few things which Intel driver doesn't support).
 However I tried to upgrade my drivers with testing branch of intel driver.
And compiz stopped working so I ckecked it with terminal and compiz.real --replace. which gives me error as:
 compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't  
 going to work.
 compiz.real (core) - Error: Failed to manage screen: 0
 compiz.real (core) - Fatal: No manageable screens found on display :0.0

and glxinfo showed that I don't have 3d rendering. 
 Can anybody help me sort it out? Does anybody had the same problem?
 Well ya one more thing then I removed that repository and driver as well still the results r same :(.
 System configuration:
 Inspiron 1525
 Intel x3100
 Ubuntu 8.04 kernel 2.6.24-23-rt

 Thank you

---

### Post by xtracool_protik on 2009-02-11
bump
 noone? or am I asking question in wrong category?

---

### Post by xtracool_protik on 2009-02-21
Guys I fixed it through upgrading to 8.10 however it doesn't seem the proper way :(

---

