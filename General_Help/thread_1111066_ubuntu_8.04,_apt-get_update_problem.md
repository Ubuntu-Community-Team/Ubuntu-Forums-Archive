---
title: "ubuntu 8.04, apt-get update problem"
date: 2009-03-30
forum: General Help
---

### Post by statmech on 2009-03-30
I cannot update the apt-get database of repositories; the
following error messages were found:

```

   [root@apollo vql]# apt-get update
   Ign http://ruslug.rutgers.edu fedora/1 release
   Ign http://download.fedora.us fedora/1/i386 release                            
   Ign http://rpm.livna.org fedora/1/i386 release                                 
   Err http://ruslug.rutgers.edu fedora/1/macromedia pkglist
     301 Moved Permanently
   Ign http://ruslug.rutgers.edu fedora/1/macromedia release                      
   Err http://ruslug.rutgers.edu fedora/1/macromedia srclist                      
     301 Moved Permanently
   Err http://download.fedora.us fedora/1/i386/os pkglist                         
     404 Not Found [IP: 152.46.7.221 80]
   Ign http://download.fedora.us fedora/1/i386/os release                

   ... cut ...

   Err http://rpm.livna.org fedora/1/i386/stable srclist
     302 Found
   Err http://rpm.livna.org fedora/1/i386/unstable srclist
     302 Found
   Err http://rpm.livna.org fedora/1/i386/testing srclist
     302 Found
   Failed to fetch http://ruslug.rutgers.edu/macromedia/apt/fedora/1/base/pkglist.macromedia  301 Moved Permanently
   Failed to fetch http://ruslug.rutgers.edu/macromedia/apt/fedora/1/base/srclist.macromedia  301 Moved Permanently

   ... cut ...

   Failed to fetch http://rpm.livna.org/fedora/1/i386/base/srclist.unstable  302 Found
   Failed to fetch http://rpm.livna.org/fedora/1/i386/base/srclist.testing  302 Found
   Reading Package Lists... Done
   Building Dependency Tree... Done
   E: Some index files failed to download, they have been ignored, or old ones used instead.
   [root@apollo vql]# 

```

It seems that the apt-get package repository web sites had been
moved.  Thanks for any info.

---

### Post by kestrel1 on 2009-03-30
This looks like Fedora, not Ubuntu.
For one thing it looks like it is trying to get RPM files not DEB.

---

### Post by statmech on 2009-03-30
> **kestrel1 said:**
> This looks like Fedora, not Ubuntu.
For one thing it looks like it is trying to get RPM files not DEB.

But I am running ubuntu 8.04...

---

### Post by atomizer on 2009-03-30
I do not understand: why do you use fedora reposetories?

i see a lot of "fedora" and "rpm" in your output.


Try to use ubuntu repo's, maybe that works

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by statmech on 2009-03-30
> **atomizer said:**
> I do not understand: why do you use fedora reposetories?

i see a lot of "fedora" and "rpm" in your output.


Try to use ubuntu repo's, maybe that works

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

You were right !! My bad ! I had several terminal windows opened
on several machines in my cluster since last week.  This morning,
when I came in, I wanted to install inkscape, and just picked out
a terminal window that I thought belonging to a machine running
ubuntu.  I was wondering why ubuntu needed fedora core rpm files...
After your e-mail, I checked my terminal window again; indeed, it
was logged into another machine running FC1.

Everything works under ubuntu now.

Thanks for your reply.

---

