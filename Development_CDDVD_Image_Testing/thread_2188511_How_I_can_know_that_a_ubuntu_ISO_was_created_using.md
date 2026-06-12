---
title: "How I can know that a ubuntu ISO was created using a live cd customization tool?"
date: 2013-11-17
forum: Development CD/DVD Image Testing
---

### Post by snfo on 2013-11-17
How I can know that a ubuntu ISO was created using a live cd  customization tool, like remastersys etc? Or how I can know that a  ubuntu ISO was created or generated?  Does live cd customization tools leave things in generated ISO?

---

### Post by ajgreeny on 2013-11-17
This may not quite answer your query, but every .iso file (and, of course, every file of any kind ever made) has its own md5sum, an alphanumeric checksum of letters and numbers which is specific for that one file; any changes to the .iso will immediately change the md5sum so you can see that it is not the original if the checksum does not match. The md5sum checksums for all available *ubuntu .iso files can be found at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")  together with information on how to use them.

---

