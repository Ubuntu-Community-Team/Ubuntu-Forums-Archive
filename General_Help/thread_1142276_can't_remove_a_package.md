---
title: "can't remove a package"
date: 2009-04-29
forum: General Help
---

### Post by leveliv on 2009-04-29
```

leveliv@leveliv-laptop:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.plA previous installation of VMware Server has been detected.

The previous installation was made by the rpm installer (version 4).

Converting the rpm4 installer database format
        to the tar4 installer database format.

You have a product that conflicts with VMware Server installed.  Continuing 
this install will first uninstall this product.  Do you wish to continue? 
(yes/no) [yes] 

error: package VMware-server is not installed
Uninstall failed.  Please correct the failure and re run the install.

Execution aborted.

```

I installed vmware with alien ...from rpm to deb ..
 
Big Mistake.  so now I am trying from tar.gz and It gives me that error..how do I remove it?

---

### Post by dcstar on 2009-04-29
> **leveliv said:**
> ```

leveliv@leveliv-laptop:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.plA previous installation of VMware Server has been detected.

The previous installation was made by the rpm installer (version 4).

Converting the rpm4 installer database format
        to the tar4 installer database format.

You have a product that conflicts with VMware Server installed.  Continuing 
this install will first uninstall this product.  Do you wish to continue? 
(yes/no) [yes] 

error: package VMware-server is not installed
Uninstall failed.  Please correct the failure and re run the install.

Execution aborted.

```

I installed vmware with alien ...from rpm to deb ..
 
Big Mistake.  so now I am trying from tar.gz and It gives me that error..how do I remove it?

With a package manager - Synaptic.

---

### Post by leveliv on 2009-04-29
> E: vmware-server: subprocess post-removal script returned error exit status 2 When I select complete remove of the package

---

