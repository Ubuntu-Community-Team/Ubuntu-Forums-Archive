---
title: "How could I do a local mirror of repositories ?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by kurtkraut on 2005-10-18
I intend to do a Install Party of Ubuntu. I won't be able to provide good internet conection for all visitors, so it would be good if I could download all packages at once and provide it thru local network by changing temporaly sources.list from visitors.

What is the easiest way to do that ? Is it possible ?

Thanks

---

### Post by DJ_Max on 2005-10-19
Have you looked at [https://wiki.ubuntu.com/LocalAptGetRepositories](https://wiki.ubuntu.com/LocalAptGetRepositories)

---

### Post by mlomker on 2005-10-19
> What is the easiest way to do that ? Is it possible ?


The entire repo for all platforms is 110 GB.  I have a repo set up at my office and I use rsync with a bunch of excludes that mostly gets me just the 32-bit files and that'll get the size down to 30 GB or so.

You'll need to create an rsynch.conf with the information/excludes that you want.  General instructions are on the [mirroring page.]("http://www.ubuntu.com/download/mirror/document_view")


```

EXCLUDE="\
  --exclude binary-amd64/ --exclude binary-powerpc/ \
  --exclude installer-amd64/ --exclude installer-powerpc/ \
  --exclude hoary*/ --exclude warty*/ \
  --exclude *_amd64.deb --exclude *_powerpc.deb \
  --exclude *.orig.tar.gz --exclude *.diff.gz --exclude *.dsc \
 " 

```

---

