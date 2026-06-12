---
title: "'Make Link' doesnt work with Windows partition"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Vulpus on 2005-11-05
When I try to use the 'Make Link' function for files in my Windows directory (hda1 and hdb1) I get the following error:

Error "Operation not permitted" while creating a link to "/media/hdb1...details.odt".

I can access them by creating a launcher on my desktop but I would be interested to know why the 'Make Link' doesnt work. It works fine with files on my Linux partition.  Am i doing something wrong or is this a 'characteristic' of Linux/Ubuntu?

---

### Post by mgor on 2005-11-05
'Make Link' is a frontend for the command 'ln' and symbolic links can not be created on/from a windows partition since it dosen't support it.

i've heard that the new version of ntfs (or maybe not until winfs comes) will support links.

---

### Post by Vulpus on 2005-11-05
I suppose it is logical when you think about.  It is not a issue as I have made a link by  creating a launcher.

---

