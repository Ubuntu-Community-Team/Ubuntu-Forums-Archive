---
title: "[SOLVED] Compiling Kopete on Debian 3.1"
date: 2006-07-26
forum: Debian
---

### Post by RavenOfOdin on 2006-07-26
Here's the deal:
Recently I tried to compile 12.1 of Kopete on Sarge, using the libxmms, libxslt and libxml2 libraries.  

Qt directories entered into ./configure correctly, --prefix as =/usr since the Kopete binary is installed in /usr/bin. 

The make process bails about 3/4 of the way because it can't find V4L2_STD_SECAM_DK.

Is there anything I might need to install or comment out to get this step working?

---

### Post by richbarna on 2006-07-27
Maybe you could try editing the make file to remove the directory that fails?
>  Locate the directory where the build fails, go one directory up and edit it's Makefile. Find the line starting with                     
```
                1:SUBDIRS=            
```
    and remove the failing directory from this list. Save and quit and start make again.

Note: this solution may not always work, maybe the directory you're excluding is required by other components of Kopete.
 
Found here:-
[http://www.kde-forum.org/drucken/14559/1/KOPETE-012-beta2-wont-start.html](http://www.kde-forum.org/drucken/14559/1/KOPETE-012-beta2-wont-start.html)

---

### Post by RavenOfOdin on 2006-07-27
I'll try that.

---

