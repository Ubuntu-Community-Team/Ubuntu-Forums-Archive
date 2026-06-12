---
title: "How to install latest version of GDM?"
date: 2005-11-08
forum: Desktop Environments
---

### Post by unixnorks on 2005-11-08
Hi guys, 

Can anyone help me find proper procedure on how to install the latest version of GDM in Ubuntu?? I have gdm-2.13.0.0 and i executed the following commands which resulted me the following error....:( 


checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.28... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

any help is highly appreciated...

God Bless!!

---

### Post by Xian on 2005-11-08
You need to install the following package:

```
$ sudo apt-cache policy libxml-parser-perl
libxml-parser-perl:
  Installed: 2.34-4
  Candidate: 2.34-4
  Version table:
 *** 2.34-4 0
        500 http://us.archive.ubuntu.com breezy/main Packages
        100 /var/lib/dpkg/status
```

---

