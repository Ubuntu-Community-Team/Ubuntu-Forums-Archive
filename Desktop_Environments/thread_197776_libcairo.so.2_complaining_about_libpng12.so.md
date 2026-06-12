---
title: "libcairo.so.2 complaining about libpng12.so"
date: 2006-06-16
forum: Desktop Environments
---

### Post by phlip on 2006-06-16
I have just installed VMware Workstation 5.5 ontop of Drake 6.06.  VMware only offers experimental support for installing on top of Ubuntu 5.10 and 5.04.

I had no problems until I updated the packages and now Workstation won't launch.  The error is:

~# /usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

I'm thinking I'd like to back out the updates, but I'm not sure how to do this.

I thought I'd use the Synaptic Package Manager, but there does not appear to be a "backout" option.  What is the backend to SPM?  Can someone point me to the command line plz?

Thanks,
Phil

---

