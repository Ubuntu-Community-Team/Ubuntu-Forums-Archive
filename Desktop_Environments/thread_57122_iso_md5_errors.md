---
title: "iso md5 errors"
date: 2005-08-15
forum: Desktop Environments
---

### Post by beebelo on 2005-08-15
I wanted to try Kubuntu (already have Ubuntu installed).  I downloaded the iso file from the official kubuntu site, and the checksum was good.   I burned the cd and used 'md5summer' to create sums and compare them to the file "md5sum.txt" that is on the root directory of the iso cd.  

Well this is a first for me, but I got three errors.  Here they are: 

.\install\netboot\pxelinux.cfg\default ERROR: 
      E:\.\install\netboot\pxelinux.cfg\default does not exists.

.\install\netboot\pxelinux.0 ERROR: Checksum did not match.

.\pool\main\m\mozilla-firefox-locale-all\mozilla-firefox-locale-en-
      gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb ERROR: 
      E:\.\pool\main\m\mozilla-firefox-locale-all\mozilla-firefox-locale-en-
      gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb does not exists.

Since two of these are 'doesn't exist' errors, I gotta doubt the errors are download or burn related.

Any advice?  Thanks.

---

### Post by beebelo on 2005-08-15
Maybe I spoke too soon.   I just realized that the 'does not exist' files are there, but are 0 byte files.  The third error relates to the file name being chopped off on my burned cd:  

"mozilla-firefox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_a" 
... and that's where the filename ends...

Well, the iso checksum matched ok before I burned it.  Is it worth a try to burn it again?

---

### Post by beebelo on 2005-08-16
I'm not the only one getting these exact md5 errors.
[http://ubuntuforums.org/showthread.php?t=19228](http://ubuntuforums.org/showthread.php?t=19228) 

Does anyone have the answer to this puzzle?  How can numerous people get the same *good* checksum on the image itself, and the same *bad* checksums on files stored *in* the image?

Any experts out there?

---

### Post by arjaybe on 2005-08-16
I'm not an expert and this isn't an answer but a question.  You didn't mention whether the cd booted.  Did it fail to boot?

---

### Post by beebelo on 2005-08-16
No, I didn't try to boot it.  I guess I figured even if it did boot or start to install, it would crash somewhere along the way.  Anyway, I tossed it, but I could burn another one -- I kept the downloaded file.

Thanks.

---

