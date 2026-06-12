---
title: "Files truncated to 32KiB when copying to smb:// path"
date: 2010-11-16
forum: Desktop Environments
---

### Post by troffasky on 2010-11-16
Trying to copy files to a smb:// resource [Windows 2008 server]. Files under 32KiB copy fine. Files larger than 32KiB get truncated to 32KiB, and then the message 

```
Could not write to file smb://user@foo/Bar.jpg
``` 

appears. Checking the share, it has actually copied the first 32KiB of the file. Using mount.cifs on the same share works fine.

Packages:

```
ii  konqueror                            4:4.5.1-0ubuntu4 
ii  libkio5                              4:4.5.1-0ubuntu8
```

This was working before upgrading to Maverick.

---

