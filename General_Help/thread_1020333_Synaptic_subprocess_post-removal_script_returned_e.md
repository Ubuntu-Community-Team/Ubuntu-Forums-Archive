---
title: "Synaptic: subprocess post-removal script returned error exit status 1"
date: 2008-12-24
forum: General Help
---

### Post by kyleabaker on 2008-12-24
I upgraded to Ubuntu 8.10 a while back and have had no problems with it other than a couple errors trying to completely remove a couple of packages.

In Synaptic Package Manager, I have two files in the "Not Installed (residual)" filter status that I am not able to remove. Is there anyway to work around this:

E: bluez-utils: subprocess post-removal script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-11-generic: subprocess post-removal script returned error exit status 1

I searched, but came up with a dead thread with the same error message:
[http://ubuntuforums.org/showthread.php?t=223071](http://ubuntuforums.org/showthread.php?t=223071)

This isn't causing problems, but it's annoying when I completely remove multiple files and get that error each time and I also just want to clean it up by getting this fixed.

Thanks in advanced.

---

### Post by dcstar on 2008-12-24
> **kyleabaker said:**
> I upgraded to Ubuntu 8.10 a while back and have had no problems with it other than a couple errors trying to completely remove a couple of packages.

In Synaptic Package Manager, I have two files in the "Not Installed (residual)" filter status that I am not able to remove. Is there anyway to work around this:

E: bluez-utils: subprocess post-removal script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-11-generic: subprocess post-removal script returned error exit status 1

I searched, but came up with a dead thread with the same error message:
[http://ubuntuforums.org/showthread.php?t=223071](http://ubuntuforums.org/showthread.php?t=223071)

This isn't causing problems, but it's annoying when I completely remove multiple files and get that error each time and I also just want to clean it up by getting this fixed.

Thanks in advanced.

Reinstall the packages and then remove them individually.

---

### Post by kyleabaker on 2008-12-24
> **dcstar said:**
> Reinstall the packages and then remove them individually.

That successfully removed blue-utils, however, the second one will not install (I was a bit skeptic about installing this module anyway, but I gave it a shot). Is there another way to clean it up without force installing or something?

Here is the install error output:

> linux-ubuntu-modules-2.6.24-11-generic:

Package linux-ubuntu-modules-2.6.24-11-generic has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by kyleabaker on 2008-12-25
Any help?

---

