---
title: "Precise: something wrong with default unzip package"
date: 2012-08-27
forum: Desktop Environments
---

### Post by doktorOblivion on 2012-08-27
I performed a full(pristine) install of the latest Precise package of XUbuntu over the weekend to find the unzip is not behaving.  In fact, my observations show it does an okay job of basic zipped text files, but on large binary files, crapola...!

For example:
$ unzip -l rtc-p2-3.0.1-repo.zip 
Archive:  rtc-p2-3.0.1-repo.zip
warning [rtc-p2-3.0.1-repo.zip]:  311848448 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  Length      Date    Time    Name
---------  ---------- -----   ----
    73776  2010-02-10 09:26   launcher

Which is of course ridiculous.  However, using 7za I am able to open and process the package without problems.

7-Zip (A) 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=de_DE.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Listing archive: rtc-p2-3.0.1-repo.zip

--
Path = rtc-p2-3.0.1-repo.zip
Type = tar
Physical Size = 311869440
Headers Size = 565248

   Date      Time    Attr         Size   Compressed  Name
------------------- ----- ------------ ------------  ------------------------
2011-11-15 13:12:24 D....            0            0  rtc-p2-3.0.1-repo
2011-06-02 07:19:58 D....            0            0  rtc-p2-3.0.1-repo/.blobstore
2011-06-02 07:17:52 D....            0            0  rtc-p2-3.0.1-repo/.blobstore/4f
2011-06-02 07:17:52 .....        75193        75264  rtc-p2-3.0.1-repo/.blobstore/4f/10c99819238d00101cbe9a7bf530aa64
2011-06-02 07:16:46 D....            0            0  rtc-p2-3.0.1-repo/.blobstore/b



HAS ANYONE ELSE SEEN THIS BEHAVIOR, and/or can explain it?  Here is the default package installation information:

ii  unzip                                   6.0-4ubuntu1                            De-archiver for .zip files

---

