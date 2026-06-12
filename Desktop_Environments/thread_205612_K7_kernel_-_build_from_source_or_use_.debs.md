---
title: "K7 kernel - build from source or use .debs?"
date: 2006-06-28
forum: Desktop Environments
---

### Post by dnovotny on 2006-06-28
I searched through the forums, and there are alot of oppinions on using the K7 kernel versus the i386 kernel, but this is not what I am looking for.  

I am using the K7 kernel on my AthlonXP2400+.  Its working well, and I am not having problems, (running XGL + Compiz, etc).  What I am wondering is if it makes sense to utilize .deb files that are compiled for i386?  I am not sure about my theory, but is it not correct that if I build any packages from source, take Wine for example, wouldn't that be built to my current kernel version, therin making the Wine package essentially a K7 version?

I understand I would of course need the kernel headers, and I would probably have to set some kernel flags somewhere, (though I don't know where) so that it would build for a K7.  

Also, if that is the case, it should be safe for me to remove the i386 kernels and headers that were installed by default right?  

If I am thinking along the right path here, about compiling my apps so they are native, could someone give me some help so that checkinstall would make K7 debs of packages I wanted to install, or point me to the appropriate places to get the information?

Thanks

---

