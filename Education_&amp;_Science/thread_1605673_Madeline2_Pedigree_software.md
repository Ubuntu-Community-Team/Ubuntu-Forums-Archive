---
title: "Madeline2 Pedigree software"
date: 2010-10-25
forum: Education &amp; Science
---

### Post by ugm6hr on 2010-10-25
Has anyone used this on 10.10 / Maverick?

It compiled correctly with a prior build (can't remember which) on 10.04, but I get the following error when running "make" on build 95 (from svn today - 25 Oct 2010)
```
finalizing index lists...
finished...
[  1%] Built target api-docs
[  1%] Built target unzip
[  1%] Generating fr.gmo
/bin/sh: GETTEXT_MSGFMT_EXECUTABLE-NOTFOUND: not found
make[2]: *** [po/fr.gmo] Error 127
make[1]: *** [po/CMakeFiles/translations.dir/all] Error 2
make: *** [all] Error 2

```
The link to the installation instructions:
[http://eyegene.ophthy.med.umich.edu/madeline/install.php](http://eyegene.ophthy.med.umich.edu/madeline/install.php)

PS: When installing libcurl-dev - I chose the libcurl4-openssl-dev version

---

### Post by ugm6hr on 2010-10-25
A lot of googling anything related to the error found these links:
[http://forum.kde.org/viewtopic.php?f=76&t=23179&start=70](http://forum.kde.org/viewtopic.php?f=76&t=23179&start=70)
[http://osdir.com/ml/file-systems.ext3.user/2004-04/msg00010.html](http://osdir.com/ml/file-systems.ext3.user/2004-04/msg00010.html)
[http://ubuntuforums.org/showthread.php?t=67088](http://ubuntuforums.org/showthread.php?t=67088)

So, then, in the /madeline2/madeline2/trunk directory:
```
sudo apt-get install build-essential gettext
./configure --with-include-gettext
make
sudo make install
```

I already had build-essential, but wanted to double-check everything.

Hope this helps someone. I've emailed them authors to let them know.

---

