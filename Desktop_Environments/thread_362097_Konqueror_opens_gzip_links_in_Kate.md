---
title: "Konqueror opens gzip links in Kate"
date: 2007-02-15
forum: Desktop Environments
---

### Post by xnd on 2007-02-15
Hello!

I'm using Kubuntu Edgy and if I click on a link with Konqueror, it opens the archive in Kate.

This applies only for weird links, ie:

[http://www.sitelliteforge.com/index/siteforge-download-action/proj.siteforge?dl=siteforge-1.0.4-stable.tar.gz](http://www.sitelliteforge.com/index/siteforge-download-action/proj.siteforge?dl=siteforge-1.0.4-stable.tar.gz)

And NOT for direct links, ie:

[http://www.something.com/archive.tar.gz](http://www.something.com/archive.tar.gz)

Any ideas?

(Fedora didn't have this.. bug or whatever)

---

### Post by kidders on 2007-02-16
Hi there,

The server hosting the tarball you posted explicitly instructs clients to treat the file as plain text.

```
wget "http://www.sitelliteforge.com/index/siteforge-download-action?proj=siteforge&step=2&dl=siteforge-1.0.4-stable.tar.gz"
--19:41:44--  http://www.sitelliteforge.com/index/siteforge-download-action?proj=siteforge&step=2&dl=siteforge-1.0.4-stable.tar.gz
           => `siteforge-download-action?proj=siteforge&step=2&dl=siteforge-1.0.4-stable.tar.gz'
Resolving www.sitelliteforge.com... 82.165.239.125
Connecting to www.sitelliteforge.com|82.165.239.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 94,239 (92K) [text/plain]

100%[====================================>] 94,239       132.42K/s
```

Unfortunately, there's not a lot you can do about other peoples' stupidity hehe.

---

