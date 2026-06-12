---
title: "removing avg75lms, how?"
date: 2009-04-22
forum: General Help
---

### Post by Saifir on 2009-04-22
Hey. 
So i installed "avg75lms-r52-a1367.i386.deb" 
Which was a package for AVG. Turned out it didn't work like I planned, and went to remove the package from add/remove applications. 
It never appeared in the list of installed aps. 
So I figured I'd just delete the files. 

It would appear that it made a directory
/opt/grisoft    /avg
                    /lib

It says I don't have the permissions to delete the files. 
The owner of /opt being root,
and the owner of /grisoft being 1009 (a group currently unassigned)

I was able to delete the files contained in these directories, but just want to delete the folders. 
Am I missing something obvious? 
I been fooling around with permissions and groups for hours!


P.s. I am a super-noob. Super noob terms are appreciated.
Thanks in advance.

---

### Post by cariboo on 2009-04-22
Open System-->Administration-->Synaptic Package Manager, and click the search button, don't use quick search, and enter avg, once synaptic finds it just mark it for complete removal and click apply.

---

