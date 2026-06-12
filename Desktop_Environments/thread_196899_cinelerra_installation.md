---
title: "cinelerra installation"
date: 2006-06-14
forum: Desktop Environments
---

### Post by werty on 2006-06-14
Hi
I wanted to install cinelerra. When i apt-get cinelerra, 
it returns this:

sujith@SUJITH:~$ sudo apt-get install cinelerra
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  cinelerra: Depends: libavc1394-0 (>= 0.5.2) but 0.5.1-1 is to be installed
             Depends: libiec61883-0 (>= 1.1.0+svn67) but it is not going to be installed
             Depends: libopenexr2c2 (>= 1.2.2) but it is not installable
             Depends: libraw1394-8 (>= 1.2.0+svn160)
E: Broken packages

Is there no support for cinelerra in dapper?

Thanks

---

### Post by cesera on 2006-06-16
What do you have in your sources.list file? When I try to install cinelerra it tells me the package doesn't exist.

---

### Post by lprofil on 2006-06-20
My Tutorial might help you:

[http://ubuntuforums.org/showthread.php?t=188264](http://ubuntuforums.org/showthread.php?t=188264)

/lprofil

---

### Post by werty on 2006-06-26
Hi
I already added the repositories when i was using breezy.
anyways thanks for tutorial. I ll try to install and tell how it went.

thanks

---

