---
title: "local filesystem file links in firefox"
date: 2009-05-11
forum: General Help
---

### Post by plh on 2009-05-11
Hi,

I don't know if it's the right place to post my problem...
Anyway, I have a question about the way firefox (I use ubuntu jaunky and firefox 3.0.10) handles the local filesystem links...

More precisely, when I enter the "file:///" URL, as expected a list of my local files / directories located under "/" is displayed. However, although clicking on most subdir links opens the selected subdir, some of them just don't react. I checked that I was the owner of thoses 'inactive' subdirs.

Any idea? Thanks in advance!

---

### Post by plh on 2009-05-12
Hi,

A friend of mine gave me the solution, and I thought it might be of some interest: the reason is that firefox disables the local link if there is a file bigger than 2GB in the directory you try to access.

Don't know why, but removing the file gave me back the correct behavior...

To whom it may concern ;-)

---

