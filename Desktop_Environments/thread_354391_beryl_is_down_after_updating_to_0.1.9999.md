---
title: "beryl is down after updating to 0.1.9999"
date: 2007-02-05
forum: Desktop Environments
---

### Post by CHNdonny on 2007-02-05
it's working in 0.1.992 ,but after updating . beryl was down.when i choose "beryl" in WINDOW MANAGEMENT,the terminal shows 
 **************************************************************
* Beryl system compatiblity check *
**************************************************************

Detected xserver : XGL

Checking Display :1.0 ...

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : passed

** (beryl-manager:9162): WARNING **: Beryl&#25318;&#25130;&#21040;&#33268;&#21629;&#20449;&#21495; 11
how can i deal with damn problem?
                                                                   thank you!

---

### Post by shareMenaPeace on 2007-02-05
If nothing helps you can try to reinstall beryl.

Check 
System -> Administration -> Synaptic Package Manager and search beryl and unmark the beryl.

Than 
```
sudo apt-get install beryl emerald-themes
```

This goes pretty fast ... i found out reinstalling made beryl more stable.

If this doesnt help try to delete the beryl folders aswell see here for more.
[http://ubuntuforums.org/showthread.php?t=354228](http://ubuntuforums.org/showthread.php?t=354228)

---

### Post by CHNdonny on 2007-02-05
thanks,i've tried reinstalling beryl even the ATI drivers but there is no use .it was normal when i used 0.1.992

---

### Post by btboudreaux on 2007-02-05
I have the same problem, reinstalling doesn't fix it. No one seems to have a solution.

---

### Post by shareMenaPeace on 2007-02-05
I read somewhere in the forum people were able to set the update back.
They done this with synaptic aswell. And checkout the offical beryl forum [http://www.beryl-project.org/](http://www.beryl-project.org/)

---

### Post by CHNdonny on 2007-02-05
thanks  but can you offer the link?

---

### Post by shareMenaPeace on 2007-02-05
Yes
[http://ubuntuforums.org/showthread.php?t=341036&highlight=beryl+update+crash](http://ubuntuforums.org/showthread.php?t=341036&highlight=beryl+update+crash)

---

### Post by shareMenaPeace on 2007-02-05
Check last post of this topic. Someone got it working....

---

### Post by CHNdonny on 2007-02-06
thank you. sharemenapeace the packages were degraded successfully.

---

