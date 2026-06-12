---
title: "Kernel compile fails due to lack of space"
date: 2009-03-29
forum: General Help
---

### Post by NuNn DaDdY on 2009-03-29
When I am trying to re-compile my kernel I receive an error at the end of the compilation notifying me that there was a lack of space or an error similar to this.  What steps can i take to be able to re-compile the kernel as I have done this a few times before already.  Is there a way to clean up space from the old kernel compiles?  Thanks!

---

### Post by ryanhaigh on 2009-03-29
I believe running the command below in the source directory will clean up temp files etc.
```
make clean
```
The other thing you can do is remove old packages from your cache using
```
sudo apt-get clean
```
If you have compiled other kernels which you aren't using any more remove them from your installation using synaptic and the source directories as well.

---

