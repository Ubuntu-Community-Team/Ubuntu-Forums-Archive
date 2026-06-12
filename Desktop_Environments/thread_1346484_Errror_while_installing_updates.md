---
title: "Errror while installing updates"
date: 2009-12-05
forum: Desktop Environments
---

### Post by kitchenware on 2009-12-05
I got the following error when installing routine bug fix updates after a fresh reboot:
     p, li { white-space: pre-wrap; }  

Error Type: 
Error Value: installArchives() failed
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1952, in 
main()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1949, in main
run(args, options.single)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1911, in run
backend.dispatcher(args)
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 647, in dispatcher
self.dispatch_command(args[0], args[1:])
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 611, in dispatch_command
self.update_packages(package_ids)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 168, in _unlock_cache_afterwards
func(*args, **kwargs)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1099, in update_packages
if not self._commit_changes(): return False
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1624, in _commit_changes
PackageKitInstallProgress(self, install_range))
File : /usr/lib/python2.6/dist-packages/apt/cache.py, line 318, in commit
raise SystemError("installArchives() failed")




$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic


$ uname -a
Linux  2.6.31.3 #1 SMP Fri Oct 9 13:23:17 BST 2009 x86_64 GNU/Linux

---

