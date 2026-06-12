---
title: "YUM repository on Ubuntu"
date: 2009-01-18
forum: General Help
---

### Post by crashcoredump on 2009-01-18
I have taken the RHCE lab and need to retake it. One of the cool things you can do with Redhat is have your own repos for updates. Having my own repo would make studying much easier.
I am sure this can be done in Ubuntu as well but I was hoping to find someone who possibly has done this.

I have the createrepo tool and have generated the .xml files.

I am just hoping there some info somewhere on this.

Any help would be great.

-J

---

### Post by RealPSL on 2009-01-18
A simplier option instead of trying to get the yum repository tools to work on Ubuntu is simply to export and NFS share to a Fedora or Red Hat system and create the repository metadata there. Once you have the metadata you can then have the repository exposed using Apache or ftp just like you would a Red Hat system. Or you could do the entire thing in a VM running on Virtual Box or VMware. This way you can focus on your studies instead of reinventing the wheel.

---

